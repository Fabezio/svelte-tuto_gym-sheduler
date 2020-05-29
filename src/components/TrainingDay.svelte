<script>
  import Details from './TrainingDayDetails.svelte'
  import Summary from './TrainingWeekSummary.svelte'
  const numOfDays = [
    {id: 1, text: "One day", value: [1]},
    {id: 2, text: "Two days", value: [1, 2]},
    {id: 3, text: "Three days", value: [1, 2 , 3]},
    {id: 4, text: "Four days", value: [1, 2, 3, 4]},
    {id: 5, text: "Five days", value: [1, 2, 3, 4, 5]},
    {id: 6, text: "Six days", value: [1, 2, 3, 4, 5, 6]},
    {id: 7, text: "Seven days", value: [1, 2, 3, 4, 5, 6, 7]}
  ] 

  const summary = []

  function handleNewExercise(event) {
    console.log("on:add-exercise", event.detail)
    summary = [...summary, event.detail]

  }

  let numDaysTrainingPerWeek

  $: console.log(numDaysTrainingPerWeek)

</script>

<form class="" action="">
  <select bind:value={numDaysTrainingPerWeek}>
    {#each numOfDays as day (day.id)}
    <option value={day}>{day.text} a week</option>
    {/each}
  </select>
</form>
<!-- <div>{JSON.stringify(numDaysTrainingPerWeek)} </div> -->
<div class="gather">
{#if numDaysTrainingPerWeek}
<div>
{#each numDaysTrainingPerWeek.value as dayNumber, i}
  <Details title={`Day ${++i}`} on:add-exercise={handleNewExercise} />
{/each}
</div>
{:else}
<div>type the right code</div>
{/if}
</div>
<Summary />
<button on:click={handleNewExercise}></button>

<style>
.gather {
  padding: .5em;
  border: medium solid green;
}

</style>


