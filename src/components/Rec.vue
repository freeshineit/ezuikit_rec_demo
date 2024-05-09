<template>
  <div style="display: flex;flex-direction: column;align-items: center;">
    <div id="video-container" style="width: 600px; height: 400px"></div>
    <div>
      <div>
        <label for="url">URL：</label>
        <input
          id="url"
          name="url"
          style="width: 500px"
          value=""
        />
      </div>
      <div>
        <label for="accessToken">accessToken</label>
        <input
          id="accessToken"
          name="accessToken"
          style="width: 500px"
          value=""
        />
      </div>
      <div>
        <label for="accessToken">domain</label>
        <input
          id="domain"
          name="domain"
          style="width: 500px"
          value="https://ieuopen.ezvizlife.com"
        />
      </div>
      <button v-on:click="handleInit">init</button>
    </div>
    <div>
      <button v-on:click="play">play</button>
      <button v-on:click="pause">pause</button>
      <button v-on:click="fullScreen">fullScreen</button>
      <button v-on:click="destroy">destroy</button>
    </div>
  </div>
</template>

<script>
import RecTheme from "@ezuikit/theme-rec";
var player = null;

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  mounted: () => {
  },
  methods: {
    init(url,accessToken, domain) {
      if (player) {
        player.destroy();
        player = null;
      }

      player = new RecTheme({
        id: "video-container", // container id
        accessToken,
        url,
        width: 600,
        height: 400,
        staticPath: '/',  // Currently, no CDN is provided. Locally specify the path of a static resource
        autoPlay: true,
        env: {domain}
      });
    },
    handleInit() {
      const url = document.getElementById("url").value;
      const accessToken = document.getElementById("accessToken").value;
      const domain = document.getElementById("domain").value;
      this.init(url, accessToken, domain);
    },
    play() {
       player.play();
    },
    pause() {
      player.pause();
    },
    fullScreen() {
      player.fullScreen();
    },
    destroy() {
      player.destroy();
      player = null;
    },
  },
};
</script>
