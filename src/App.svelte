<!-- Scrupt -->
<script lang="ts">
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
<section
  class="w-full h-screen bg-indigo-400 flex flex-col justify-start px-5 sm:pt-8 sm:items-center"
>
  <h1 class="pt-20 pb-5 text-4xl text-yellow-200 font-bold">Todos</h1>

  {#each todos as todo}
    <div
      class:done={todo.done}
      class="w-4/5 grid grid-cols-10 mb-3 max-w-screen-sm"
    >
      <input
        class="self-center place-self-end mr-3 bg-yellow-50 w-1/2 h-1/2 border-4 sm:place-self-center cursor-pointer"
        type="checkbox"
        bind:checked={todo.done}
      />
      <input
        class="p-2 col-span-9 h-10 text-indigo-800 placeholder-indigo-400 bg-yellow-50 focus:bg-yellow-400 text-2xl"
        placeholder="What needs to be done?"
        bind:value={todo.text}
      />
    </div>
  {/each}

  <p class="text-yellow-50 text-lg">
    {remaining ? `${remaining} remaining` : 'done'}
  </p>

  <button
    class="w-full bg-purple-300 hover:bg-purple-600 my-2 text-yellow-50 text-2xl h-10 border-purple-900 hover:text-yellow-200 max-w-screen-sm"
    on:click={add}
  >
    Add new
  </button>

  <button
    class="w-full bg-purple-300 hover:bg-purple-600 text-yellow-50 text-2xl h-10 border-purple-900 hover:text-yellow-200 max-w-screen-sm"
    on:click={clear}
  >
    Clear completed
  </button>
</section>

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
  }
</style>
