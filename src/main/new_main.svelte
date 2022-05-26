<script>
  let isEdit = true;
  let videourl, newVideo, newVideoSrc;
  const file = 'videos/SampleVideo_1280x720_10mb.avi';
  const videos = [
    '소방시연용_Remote_mov_201103_lite',
    'CPR add-on ki t Class _ 상황별 교육을 위한 새로운 솔루션',
    'cprCUBE_pro_mov_201103_01_kor',
    'IMLAB 소개영상 _50s',
    'UAOK_guide_mov_kor_200403',
    '이중의교수님의 cprCUBE 리뷰 - 짧은버전',
  ];

  function togleEdit() {
    isEdit = !isEdit;
  }
  function handleFileSelected(event) {
    const video = event.target.files[0];
    videourl = URL.createObjectURL(video);
    console.log(videourl);
  }
</script>

<article>
  {#if !isEdit}
    <header>
      <div>
        <img src="images/CLS_logo_red.svg" alt="logo-class" />
      </div>
      <div>
        <img src="images/Frame 144.svg" alt="logo-class" />
      </div>
    </header>
  {/if}
  <main>
    {#if !isEdit}
      <section id="menu-section">
        <div id="menu-label">
          <span>Menu</span>
        </div>
        <div id="menu-video-container">
          <div class="menu-video">
            <div class={isEdit ? 'edit-page' : 'main-page'}>video</div>
            <div class={isEdit ? 'edit-page' : 'main-page'}>
              <img src="images/i_feedback_2t.svg" alt="logo-class" />
              <span>Feedback mode</span>
            </div>
          </div>
          <div class="menu-video">
            <div class={isEdit ? 'edit-page' : 'main-page'}>video</div>
            <div class={isEdit ? 'edit-page' : 'main-page'}>
              <img src="images/i_mission_L.svg" alt="logo-class" />
              <span>Mission Mode</span>
            </div>
          </div>
          <div class="menu-video">
            <div class={isEdit ? 'edit-page' : 'main-page'}>video</div>
            <div class={isEdit ? 'edit-page' : 'main-page'}>
              <img src="images/i_result_2t.svg" alt="logo-class" />
              <span>Results</span>
            </div>
          </div>
        </div>
      </section>
    {/if}
    <section id="lectures-section">
      <div id="lectures-label">
        <span>Lectures</span>
        <div>
          {#if isEdit}
            <div on:click={togleEdit} id="edit-out-button1">
              <span>Cancel</span>
            </div>
            <div on:click={togleEdit} id="edit-out-button2">
              <img src="images/i_edit_white.svg" alt="logo-class" />
              <span>Done</span>
            </div>
          {:else}
            <div on:click={togleEdit} id="edit-in-button">
              <img src="images/i_edit_s.svg" alt="logo-class" />
              <span>Edit</span>
            </div>
          {/if}
        </div>
      </div>
      <div id="lectures-video-container">
        {#each videos as video}
          <div class="lectures-video">
            <div class={isEdit ? 'edit-page' : 'main-page'}>
              <!-- svelte-ignore a11y-media-has-caption -->
              <video controls src={`videos/${video}.mp4`} />
            </div>
            <span>{video.slice(0, 28)}</span>
            {#if isEdit}
              <button><img src="images/Icon button.svg" alt="" /></button>
            {/if}
          </div>
        {/each}
        {#if videourl}
          <div class="lectures-video">
            <div class={isEdit ? 'edit-page' : 'main-page'}>
              <!-- svelte-ignore a11y-media-has-caption -->
              <video autoplay controls src={videourl} />
            </div>
            <span>test</span>
            {#if isEdit}
              <button><img src="images/Icon button.svg" alt="" /></button>
            {/if}
          </div>
        {/if}

        {#if isEdit}
          <div class="lectures-video add-video">
            <div />
            <label for="new-video">
              <img src="images/Frame 1771.svg" alt="" />
              <input
                id="new-video"
                type="file"
                accept="video/*"
                on:change={handleFileSelected}
              />
            </label>
          </div>
        {/if}
      </div>
    </section>
  </main>
</article>

<style lang="scss">
  article {
    background-color: rgb(224, 245, 184);
    padding: 20px 24px;
    min-height: 100vh;
  }
  header {
    display: flex;
    justify-content: space-between;
    height: 60px;
    margin-bottom: 31px;
    div:first-child {
      img {
        width: 278px;
        height: 25px;
        margin: 17.5px 16px;
      }
    }
    div:last-child {
      img {
        width: 60px;
        height: 60px;
        cursor: pointer;
      }
    }
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
      width: 215px;
      height: 41px;
      display: flex;
      justify-content: flex-end;
      gap: 15px;

      div {
        width: 100px;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 4px;
        border-radius: 99px;
        background-color: white;
        cursor: pointer;
        img {
          width: 25px;
          height: 25px;
        }
        span {
          font-size: 19px;
        }
      }
      #edit-out-button1 {
        border: solid 2px #c84637;

        color: #c84637;
      }
      #edit-out-button2 {
        border: solid 2px #c84637;

        img {
          color: #f3f3f3;
        }
        color: #f3f3f3;
        background-color: #c84637;
      }
      #edit-in-button {
        border: solid 2px #666666;
        color: #585858;
      }
    }
  }
  #menu-video-container,
  #lectures-video-container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
    @media screen and (max-width: 1990px) {
      grid-template-columns: 1fr 1fr 1fr 1fr;
    }
    @media screen and (max-width: 1490px) {
      grid-template-columns: 1fr 1fr 1fr;
    }
    @media screen and (max-width: 990px) {
      grid-template-columns: 1fr 1fr;
    }
    @media screen and (max-width: 490px) {
      grid-template-columns: 1fr;
    }
    gap: 32px 8px;
    width: 100%;
    & > div {
      min-width: 250px;
      max-width: 500px;
      display: flex;
      flex-direction: column;
      position: relative;
      & > div:first-child {
        width: 100%;
        aspect-ratio: 16 / 9;
        border: solid 2px #666666;

        // video
        border-radius: 12px;
      }
      .main-page {
        cursor: pointer;
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
      border: solid 2px #666666;

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
    button {
      position: absolute;
      top: 8px;
      right: 8px;
      width: 28px;
      height: 28px;
      z-index: 5;
    }
  }
  .add-video {
    & > div {
      border: solid 2px #666666;
    }
    input {
      display: none;
    }
    img {
      cursor: pointer;
      width: 45px;
      height: 45px;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -80%);
    }
  }
</style>
