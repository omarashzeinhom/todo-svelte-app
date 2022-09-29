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

<footer>
  @ANDGOEDU OmarZeinhom & Svelte DOCS
</footer>