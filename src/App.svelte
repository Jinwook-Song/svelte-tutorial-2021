<!-- Scrupt -->
<script>
  let todos = [
    { done: false, text: 'finish Svelte tutorial' },
    { done: false, text: 'build an app' },
    { done: false, text: 'world domination' },
  ];

  function add() {
    todos = todos.concat({ done: false, text: '' });
  }

  function clear() {
    todos = todos.filter((todo) => !todo.done);
  }

  $: remaining = todos.filter((todo) => !todo.done).length;
</script>

<!-- Markup -->
<h1 class="bg-pink-300">Todos</h1>

{#each todos as todo}
  <div class:done={todo.done}>
    <input type="checkbox" bind:checked={todo.done} />
    <input placeholder="What needs to be done?" bind:value={todo.text} />
  </div>
{/each}

<p>{remaining ? `${remaining} remaining` : 'done'}</p>

<button on:click={add}> Add new </button>

<button on:click={clear}> Clear completed </button>

<!-- Style -->
<style lang="scss">
  .done {
    opacity: 0.4;
    input {
      text-decoration-line: line-through;
    }
  }
  input:last-child {
    border-radius: 5px;
  }
  button {
    border-color: transparent;
    &:hover {
      background-color: antiquewhite;
    }
  }
</style>
