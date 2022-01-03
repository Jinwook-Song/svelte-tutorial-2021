<script lang="ts">
  import type { ITodo } from '../types/ITodo';
  export let todo: ITodo;

  let isEdit = false;
  let title = '';

  function onEdit() {
    isEdit = true;
    title = todo.title;
  }
  function offEdit() {
    isEdit = false;
  }
  function updateTodo() {
    todo.title = title;
    offEdit();
  }
  function deleteTodo() {}
</script>

{#if isEdit === true}
  <div>
    <input
      type="text"
      bind:value={title}
      on:keydown={(e) => {
        e.key === 'Enter' && updateTodo();
      }}
    />
    <button on:click={updateTodo}>OK</button>
    <button on:click={offEdit}>Cancel</button>
  </div>
{:else if isEdit === false}
  <div>
    {todo.title}
    <button on:click={onEdit}>Edit</button>
    <button on:click={deleteTodo}>Delete</button>
  </div>
{/if}
