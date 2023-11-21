<script lang="ts">
  let todoText = ""
  let todos = ["todo 1", "todo 2", "todo 3"]

  function addTodo () {
    if (!todoText) return
    todos.push(todoText)
    todos = todos
    todoText = ""
  }

  function deleteTodo (id: number) {
    todos.splice(id, 1)
    todos = todos
  } 
</script>

<div class="container">
  <h1 class="header">Todo</h1>
  <div class="flex">
    <input type="text" placeholder="Add Todo..." bind:value={todoText}>
    <button on:click={addTodo}>Add</button>
  </div>
  <ul class="todos">
    {#each todos as todo, i}
      <li>{todo} <button on:click={() => deleteTodo(i)}>Delete</button></li>
    {/each}
  </ul>
</div>

<style>
  

  .container {
    font-family: sans-serif;
    max-width: 600px;
    margin: 2rem auto;
  }

  .flex {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
  }

  .flex input {
    flex: 2;
    padding: 5px;
  }

  .flex button {
    padding: 5px 8px;
  }

  .header {
    text-align: center;
    font-size: 2rem;
  }

  .todos {
    list-style-type: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
    align-items: center;
  }
  
</style>