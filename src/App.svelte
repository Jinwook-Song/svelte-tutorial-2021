<script lang="ts">
  loop1: for (let i = 1; i < 4; i++) {
    loop2: for (let j = 1; j < 4; j++) {
      if (i === 2) {
        break loop1;
      }
      console.log(`${i}-${j}`);
    }
    console.log('-------');
  }

  jw: {
    console.log('a');
    break jw;
    console.log('b');
  }

  // Svelte 반응성 구문
  let count = 0;
  $: {
    console.log(count);
  }
</script>
