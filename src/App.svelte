<script lang="ts">
  import type { ITodo } from './types/ITodo';
  import Todo from './components/Todo.svelte';

  let title = '';
  let todos: ITodo[] = [];

  function createTodo() {
    todos.push({
      id: Date.now(),
      title,
    });
    todos = todos; // 할당을 통해 반응성을 유도
    title = ''; // input 값 비우기
  }
  console.log(todos);
</script>

<input
  type="text"
  bind:value={title}
  on:keydown={(e) => e.key === 'Enter' && createTodo()}
/>
<button on:click={createTodo}>Create Todo</button>

{#each todos as todo}
  <Todo {todo} />
{/each}
