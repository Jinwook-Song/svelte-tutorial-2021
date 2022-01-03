[Svelte](https://svelte.dev/)

[Svelte.js 완벽 가이드(Renew)](https://heropy.blog/2019/09/29/svelte/)

- Core concept
  - Write less code
    - 높은 가독성 유지
    - 개발 시간 단축
    - 쉬운 리팩토링
    - 쉬운 디버깅
    - 더 작은 번들(SPA 최적화)
    - 낮은 러닝 커브
  - No virtual DOM
    - No Diffing
      - Diffing이란 Virtual DOM에서 서로 비교하여 차이가 있는 부분만 업데이트 하는 방식
      - 비교를 위해서는 새로운 Virtual DOM을 생성해야하고, 그 결과를 실제 DOM에 갱신
      - Svelte의 경우 갱신만 해주면 된다
    - No Overhead
      - 어떤 처리를 위해 들어가는, 간접적인 시간이나 메모리
      - VIrtual DOM을 통한 추가적인 loss가 발생하지 않음
    - 빠른 성능(퍼포먼스)
      - 예시) Result of memory usage
        - React: 30 ~ 110 MB
        - Svelt: 15 ~ 30 MB
  - Truly reactive
    - Framework-less VanillaJS, Only use ‘devDependencies’
      - Svelte가 어플리케이션을 VanillaJS로 컴파일하고 그 결과만 동작하기 때문에, Svelte는 브라우저(런타임)에서 동작하지 않는 컴파일러라고 할 수 있다.
  - 명시석 설계(창의적 작업)
- 단점 (2019. 4 기준)
  낮은 성숙도(작은 커뮤니티)
  CDN 미제공 (런타임에서 동작하지 않기 때문에)
  IE 미지원

# 시작하기

```bash
npx degit sveltejs/template my-svelte-project
cd my-svelte-project
npm install
npm run dev
```

- 타입스크립트 적용
  `node ./scripts/setupTypeScript.js` 위 명령어를 통해 타입스크립트를 적용할 수 있습니다.
  setupTypeScript는 템플릿을 다운 받을때 타입스크립트 적용을 위한 기본 파일입니다.

# Todo demo with typescript

- Tree 구조
  ```jsx
  ├── App.svelte
  ├── components
  │   └── Todo.svelte
  ├── global.d.ts
  ├── main.ts
  └── types
      └── ITodo.ts
  ```

## Create Todos

- App.svelte
  ```jsx
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
  ```
- Todo.svelte
  ```jsx
  <script lang="ts">
    import type { ITodo } from '../types/ITodo';
    export let todo: ITodo;
  </script>

  <div>
    {todo.title}
  </div>
  ```
- Types
  ```jsx
  export interface ITodo {
    id: number;
    title: string;
  }
  ```

## Update & Delte Todos

todos 배열은 App.svelte에 정의되어 있습니다.

따라서 todos를 삭제하는 경우, 반응성을 유도하기 위해 props를 건내줄 때 bind를 사용할 수 있습니다.

본 예제에서는 bind대신 store를 활용하였습니다.

- App.svelte
  ```jsx
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
  ```
- Todo.svelte
  ```jsx
  <script lang="ts">
    import type { ITodo } from '../types/ITodo';
    import type { Writable } from 'svelte/store';

    export let todos: Writable<ITodo[]>;
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
    function deleteTodo() {
      $todos = $todos.filter((t) => t.id !== todo.id);
    }
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
  ```
