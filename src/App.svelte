<script lang="ts">
  import { tick } from 'svelte';

  let count = 0;
  let double = 0;

  // Label 구문
  // 반응성 구문 내에 반응성을 갖는 변수 명시
  $: {
    double = count * 2;
    console.log('double!', double);
  }
  $: double2 = count * 2;

  /* 'count 값 변경된 후 대기 로직이 처리되고,
   화면이 갱신되어야 반응성 구문($:)이 실행된다.' */
  async function assgin() {
    count++;
    console.time('tiemr');
    await tick(); // 반응성을 기다림
    console.timeEnd('tiemr');
    console.log(double);
  }
</script>

<button on:click={assgin}>Assing</button>
<h2>{count}</h2>
<h2>{double}</h2>
<h2>{double2}</h2>
