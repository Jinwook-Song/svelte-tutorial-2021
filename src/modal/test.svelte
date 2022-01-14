<script>
  let counts = "1,2".split(",");
  let spares = "1,2,3,4,5,6,7,8,9".split(",");
</script>

{#if true}
  <div id="modal-wrapper">
    <header id="dongle-modal-header">
      <img src={"images/dongle_header.svg"} alt="dongle-header" />
    </header>
    <section id="dongle-modal-body">
      <div id="dongle-logo">
        <img src={"images/img_donglemanager.svg"} alt="dongle-manager" />
      </div>
      <div id="dongle-announcement">
        <span>Please connect the Class dongles you have.</span>
      </div>
      <div id="dongle-connected-status-image">
        {#each spares as spare}
          {#if counts.length >= spare}
            <img src={"images/dongle_checked.svg"} alt="dongle-checked" />
          {:else}
            <div id="dongle-spares" />
          {/if}
        {/each}
      </div>
      <div id="dongle-connected-status-message">
        <span>{counts.length} dongles connected</span>
        <span
          >You can connect up to {counts.length * 5} CPR devices with {counts.length}
          dongles.</span
        >
      </div>
      <div id="dongle-line" />
      <div id="dongle-btn">
        <button id="cancel-btn">Cancel</button>
        <button id="done-btn">Done</button>
      </div>
    </section>
  </div>
{/if}

<style>
  #modal-wrapper {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 576px;
    border-radius: 8px;
    margin: 0;
    background-color: #fff;
    opacity: 1 !important;
    box-shadow: 0 0 16px rgba(0, 0, 0, 0.25);
    z-index: 200;
  }
  #dongle-modal-header img {
    width: 576px;
    height: 42px;
  }
  #dongle-modal-body {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  #dongle-logo img {
    width: 244px;
    height: 144px;
  }
  #dongle-announcement {
    width: 576px;
    height: 70px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: bold;
    font-size: 15px;
    line-height: 21px;
    letter-spacing: 0.3px;
  }
  #dongle-connected-status-image {
    width: 100%;
    padding: 0 60px;
    display: flex;
    justify-content: space-between;
    margin-bottom: 13px;
  }
  #dongle-connected-status-image * {
    width: 40px;
    height: 40px;
    background-color: #dadada;
    border-radius: 100%;
  }
  #dongle-connected-status-message {
    display: flex;
    flex-direction: column;
    color: #585858;
    font-size: 15px;
    line-height: 21px;
    letter-spacing: 0.3px;
    margin-bottom: 10px;
  }
  #dongle-line {
    width: 560px;
    height: 1px;
    background-color: #dadada;
  }
  #dongle-btn {
    width: 100%;
    height: 45px;
    display: flex;
    justify-content: space-around;
    color: #c84637;
    font-size: 15px;
    line-height: 21px;
    letter-spacing: 0.1px;
    position: relative;
  }
  #dongle-btn #done-btn {
    font-weight: bold;
    cursor: pointer;
  }
  #dongle-btn #done-btn::before {
    content: "";
    position: absolute;
    top: 0;
    left: 50%;
    width: 1px;
    height: 44.8px;
    transform: rotate(180deg);
    background-color: #dadada;
  }
</style>
