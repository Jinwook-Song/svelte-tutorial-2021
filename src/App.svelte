<script lang="ts">
  import type { ITodo } from './types/ITodo';
  import { writable } from 'svelte/store';
  import Todo from './components/Todo.svelte';

  let title = '';
  // todos 는 단순 배열이 아닌 store 객체가 됩니다.
  let todos = writable<ITodo[]>([]);

  function createTodo() {
    // input 값이 없는 경우 return
    if (!title.trim()) {
      title = '';
      return;
    }
    $todos.push({
      id: Date.now(),
      title,
    });
    $todos = $todos; // 할당을 통해 반응성을 유도합니다.
    title = ''; // input 값 flush
  }
</script>

<input
  type="text"
  bind:value={title}
  on:keydown={(e) => e.key === 'Enter' && createTodo()}
/>
<button on:click={createTodo}>Create Todo</button>

{#each $todos as todo}
  <Todo {todos} {todo} />
{/each}
