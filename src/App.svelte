<script>
  import AddItem from "./components/AddItem.svelte";
  import TodoItem from "./components/TodoItem.svelte";

  let todoList = [];

  function addItem(event) {
    if (event.detail.value?.length > 0) {
      todoList = [
        ...todoList,
        {
          key: Math.floor(Math.random() * 10000000),
          item: event.detail.value,
        },
      ];
    } else {
      alert("Sorry, can't add empty items!");
    }
  }

  function removeItem(event) {
    todoList = todoList.filter((todo) => todo.key !== event.detail.key);
  }
</script>

<div class="container">
  <h1 class="text-center mt-5 mb-5 text-light">Svelte ToDo App</h1>

  <div id="todo-container" class="bg-light p-4">
    <AddItem buttonLabel="Add Item" on:addItem={addItem} />
    {#if todoList.length > 0}
      {#each todoList as todo, i (todo.key)}
        <TodoItem
          todoItem={todo.item}
          todoKey={todo.key}
          on:done={removeItem}
        />
      {/each}
    {/if}
  </div>
</div>

<style>
  #todo-container {
    border-radius: 6px;
  }
</style>
