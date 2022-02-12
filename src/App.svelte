<script lang="ts">
  let count = 0;
  let double = 0;

  function assgin() {
    count++;
  }
</script>

{@debug count}
<button on:click={assgin}>Assign</button>
<h2>{count}</h2>
<h2>{double}</h2>
