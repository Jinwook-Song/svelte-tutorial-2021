<script>
  export let modalActive = false;

  function close() {
    modalActive = false;
  }
</script>

{#if modalActive}
  <div class="modal-background" on:click={close} />

  <div class="modal" role="dialog" aria-modal="true">
    <slot name="header" />
    <hr />
    <slot name="content" />
    <hr />

    <!-- svelte-ignore a11y-autofocus -->
    <button autofocus on:click={close}>close modal</button>
  </div>
{/if}

<style>
  .modal-background {
    width: 100vw;
    height: 100vh;
    -webkit-backdrop-filter: blur(4px);
    backdrop-filter: blur(4px);
    background-color: rgba(0, 0, 0, 0.2);
  }

  .modal {
    position: absolute;
    left: 50%;
    top: 50%;
    width: calc(100vw - 4em);
    max-width: 32em;
    max-height: calc(100vh - 4em);
    overflow: auto;
    transform: translate(-50%, -50%);
    padding: 1em;
    border-radius: 0.2em;
    background: white;
  }

  button {
    display: block;
  }
</style>
