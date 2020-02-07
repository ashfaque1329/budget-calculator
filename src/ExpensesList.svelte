<script>
  import SectionTitle from "./Title.svelte";
  import Expense from "./Expense.svelte";
  export let expenses = [];
  console.log("expenses2:", expenses);
</script>

<style>
  h2 {
    text-transform: capitalize;
  }
</style>

<section>
  <SectionTitle title="expense list" />
  <ul>
    {#each expenses as expense, index}
      <Expense {expense} />
    {:else}
      <h2>Sorry, no expense for you!</h2>
    {/each}
  </ul>

</section>
