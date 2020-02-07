<script>
  import { setContext } from "svelte";
  import Navbar from "./Navbar.svelte";
  import ExpensesList from "./ExpensesList.svelte";
  import expensesData from "./expenses";

  let expenses = [...expensesData];
  console.log(expenses);

  function removeExpense(id) {
    expenses = expenses.filter(item => item.id !== id);
    console.log(expenses);
  }

  setContext("remove", removeExpense);
</script>

<Navbar />
<main class="content">
  <ExpensesList {expenses} />
</main>
