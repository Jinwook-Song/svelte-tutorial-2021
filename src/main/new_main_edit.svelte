<script>
</script>

<article>
  <main>
    <section id="lectures-section">
      <div id="lectures-label">
        <span>Lectures</span>
        <div>
          <img src="images/i_edit_s.svg" alt="logo-class" />
          <span>Edit</span>
        </div>
      </div>
      <div id="lectures-video-container">
        <div class="lectures-video">
          <div>video</div>
          <span>Call 911</span>
        </div>
        <div class="lectures-video">
          <div>video</div>
          <span>Call 911</span>
        </div>
        <div class="lectures-video">
          <div>video</div>
          <span>Call 911</span>
        </div>
        <div class="lectures-video">
          <div>video</div>
          <span>Call 911</span>
        </div>
        <div class="lectures-video">
          <div>video</div>
          <span>Call 911</span>
        </div>
      </div>
    </section>
  </main>
</article>

<style lang="scss">
  article {
    background-color: rgb(224, 245, 184);
    padding: 20px 24px;
    height: 100vh;
  }
  main {
    display: flex;
    flex-direction: column;
    gap: 36.6px;
  }
  section {
    display: flex;
    flex-direction: column;
    gap: 7px;
  }
  #menu-label,
  #lectures-label {
    display: flex;
    justify-content: space-between;
    & > span {
      font-size: 29px;
    }
    & > div {
      width: 89px;
      height: 41px;
      display: flex;
      justify-content: center;
      align-items: center;
      border: solid 1px black;
      border-radius: 99px;
      gap: 4px;
      background-color: white;
      cursor: pointer;
      img {
        width: 25px;
        height: 25px;
      }
      span {
        font-size: 19px;
        color: #585858;
      }
    }
  }
  #menu-video-container,
  #lectures-video-container {
    display: flex;
    flex-wrap: wrap;
    gap: 24px 8px;
    & > div {
      display: flex;
      flex-direction: column;
      position: relative;
      & > div:first-child {
        // video
        cursor: pointer;
        width: 342px;
        height: 192.4px;
        background-color: #171717;
        border-radius: 12px;
      }
    }
  }
  #menu-video-container > div {
    & > div:last-child {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 8px;
      width: 100%;
      height: 61px;
      position: absolute;
      bottom: 0;
      background-color: white;
      border-radius: 0 0 12px 12px;
      img {
        width: 45px;
        height: 45px;
      }
      span {
        font-size: 22px;
      }
    }
  }

  #lectures-video-container > div {
    span {
      font-size: 19px;
      color: #585858;
      margin-left: 8px;
    }
  }
</style>
