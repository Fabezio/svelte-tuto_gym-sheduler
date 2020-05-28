<script>
  const numOfDays = [
    {id: 1, text: "One day", value: 1},
    {id: 2, text: "Two days", value: 2},
    {id: 3, text: "Three days", value: 3},
    {id: 4, text: "Four days", value: 4},
    {id: 5, text: "Five days", value: 5},
    {id: 6, text: "Six days", value: 6},
    {id: 7, text: "Seven days", value: 7}
  ]

  let numDaysTrainingPerWeek

  $: console.log(numDaysTrainingPerWeek)

</script>

<form action="">
  <select bind:value={numDaysTrainingPerWeek}>
    {#each numOfDays as day (day.id)}
    <option value={day}>{day.text}</option>
    {/each}
  </select>
</form>
<div>{JSON.stringify(numDaysTrainingPerWeek)} </div>

<style>

</style>


