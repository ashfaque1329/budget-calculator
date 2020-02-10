<script>
  import { setContext } from "svelte";
  import Navbar from "./Navbar.svelte";
  import ExpenseForm from "./ExpenseForm.svelte";
  import Totals from "./Totals.svelte";
  import ExpensesList from "./ExpensesList.svelte";
  import expensesData from "./expenses";

  let expenses = [...expensesData];
  console.log(expenses);

  $: total = expenses.reduce((acc, curr) => {
    return (acc += curr.amount);
  }, 0);

  function removeExpense(id) {
    expenses = expenses.filter(item => item.id !== id);
    console.log(expenses);
  }

  function deleteExpense(event) {
    const { id } = event.detail;
    removeExpense(id);
  }

  function clearExpenses() {
    expenses = [];
  }

  function addExpense({ name, amount }) {
    let expense = { id: Math.random() * Date.now(), name, amount };
    expenses = [expense, ...expenses];
    //expenses.push(expense);
    console.log(expenses);
  }
  setContext("remove", removeExpense);
</script>

<Navbar />
<main class="content">
  <ExpenseForm {addExpense} />
  <Totals title="total expenses" {total} />
  <ExpensesList {expenses} on:delete={deleteExpense} />
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}>
    clear expenses
  </button>
</main>
