<script>
  import Parent from './Parent.svelte';
  import { storeName } from './store';

  let name = 'jinwook';
  $storeName = name;

  // Auto subscription
  console.log($storeName);
</script>

<h1>{name} App</h1>
<Parent />
