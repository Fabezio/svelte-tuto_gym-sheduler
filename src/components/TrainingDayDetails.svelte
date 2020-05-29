<script>
  export let title;
  import { createEventDispatcher } from 'svelte'
  let exercise = {
    activity: "",
    sets: 4,
    reps: 10
  };
  let dispatch = createEventDispatcher()
  let exercises = [];
  function handleSubmit() {
    exercises = [...exercises, { ...exercise }];
    dispatch('add-exercise', {...exercise, title: title})
    exercise = {
      activity: "",
      sets: 4,
      reps: 10
    };
  }
  function stringify(object) {
    return JSON.stringify(object);
  }
  function stringifyArray(array) {
    let res = [];
    for (let obj of array) {
      res = [...res, stringify(obj)];
    }
    return res;
  }
  // dispatch('stringifyArray', stringifyArray())
</script>



<div class="detail">
  <h2>{title}</h2>
  <div>
    <form on:submit|preventDefault={handleSubmit}>
      <div>
        <label for="activity">Activity</label>
        <input type="text" id="activity" bind:value={exercise.activity} />
      </div>
      <div>
        <label for="sets">Sets</label>
        <input type="number" id="sets" bind:value={exercise.sets} />
      </div>
      <div>
        <label for="reps">Reps</label>
        <input type="number" id="reps" bind:value={exercise.reps} />
      </div>
      <button type="submit">add exercise</button>
    </form>
  </div>
  <!-- <div>exercise: {stringify(exercise)} </div> -->
  {#each exercises as ex, i}
  <div>{ex.activity}: {ex.sets} sets of {ex.reps}</div>
  {/each}
  

</div>

<style>
.detail {
  padding: 0.5em;
  border: medium solid purple;
  margin-bottom: 0.5em;
}
</style>