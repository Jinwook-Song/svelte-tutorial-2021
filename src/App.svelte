<script lang="ts">
  let name = 'jinwook';
  let array = ['a', 'b', 'c'];

  function assign() {
    name = 'nico';
    // array.push('d');
    // array = array;
    array = [...array, 'd'];
  }
</script>

<button on:click={assign}>Assign</button>

<h2>name: {name}</h2>
<h2>array: {array}</h2>
