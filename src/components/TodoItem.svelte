<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let todoItem;
  export let todoKey;

  let status = false;

  $: if (status)
    dispatch("done", {
      key: todoKey,
    });
</script>

<div class="form-check todo-item ml-2 mt-4">
  <input
    class="form-check-input"
    id={todoKey}
    type="checkbox"
    bind:checked={status}
  />
  <label for={todoKey}>
    {todoItem}
  </label>
</div>
