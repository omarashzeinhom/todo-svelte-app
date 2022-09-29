<script>
  import svelteLogo from "./assets/svelte.svg";
  //TODO Scripts
  var poweredBy = "Powered By";
  var pageTitle = "To Do App";
  var newItem = "";

  var todoList = [
    { text: "Build A Svelte ToDoApp From Docs", status: true },
    { text: "Upload the Video To Youtube", status: false },
    { text: "Check Content Replies", status: false },
  ];

  function addToList() {
    todoList = [...todoList, { text: newItem, status: false }];
    newItem = "";
  }

  function removeFromList(index) {
    todoList.splice(index, 1);
    todoList = todoList;
  }
</script>

<section>
  <a href="https://svelte.dev" target="_blank">
    {poweredBy}<img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
  </a>
  <h1>{pageTitle}</h1>

  <input bind:value={newItem} type="text" placeholder="Add New ToDo Here..." />
  <button on:click={addToList}>Add</button>

  <br />
  {#each todoList as item, index}
    <input bind:checked={item.status} type="checkbox" />
    <span class:checked={item.status}>{item.text}</span>
    <span on:click={() => removeFromList(index)}>❌</span>
    <br />
  {/each}
</section>

<style>
  section {
    background-color: #1111;
    opacity: 80%;
    padding: 1rem 1rem 1rem 1rem;
    max-height: 100vh;
    border-radius: 0.4rem;
    border: solid 0.1rem #ff3e00aa;
  }

  .checked {
    text-decoration: line-through green 0.2rem;
  }
  .closeBtn {
    cursor: pointer;
  }
  button {
    background-color: green;
  }
  input {
    padding: 1rem 1rem 1rem 1rem;
    border-radius: 0.4rem;
    transition: 0.3s ease-in-out;
  }
  input:hover {
    background-color: green;
    color: white;
  }
  .logo {
    width: 100%;
    height: 6rem;
    padding: 1.5em;
    will-change: filter;
    justify-content: center;
    text-align: center;
    display: grid;
    grid-template-columns: 1fr;
    color: white;
    transition: 0.4s ease-in-out;
  }

  a {
    color: #ff3e00aa;
    transition: 0.4s ease-in-out;
  }
  a:hover {
    color: whitesmoke;
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2rem #ff3e00aa);
  }
</style>
