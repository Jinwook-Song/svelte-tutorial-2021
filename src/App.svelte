<script lang="ts">
  let count = 0;

  // 선언
  $: double = count * 2;

  // 블록
  $: {
    console.log(count);
    console.log(double);
  }

  // 함수 실행
  $: count, log();

  // 즉시 실행 함수 (IIFE)
  $: count,
    (() => {
      console.log('즉시 실행');
    })();

  // 조건문 (if)
  $: if (count > 0) {
    console.log('if', double);
  }

  // 반복문 (for)
  $: for (let i = 0; i < 3; i++) {
    count;
    console.log('for', i);
  }

  // 조건문 (switch)
  $: switch (count) {
    case 1:
      console.log('switch: 1');
      break;
    case 2:
      console.log('switch: 2');
      break;
    default:
      console.log('switch: default');
  }

  // 유효범위
  $: {
    function scope1() {
      console.log('scope1');
      function scope2() {
        console.log('scope2');
        function scope3() {
          console.log('scope3', count);
        }
        scope3();
      }
      scope2();
    }
    scope1();
  }

  function log() {
    console.log('fn: log');
  }
  function assing() {
    count++;
  }
</script>

<button on:click={assing}>Assing!</button>
