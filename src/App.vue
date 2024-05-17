<template>
  <p>Vimeo player:</p>
  <div ref="vimeoPlayerContainer"></div>
  <p>Is player ready: <span v-if="isPlayerReady">true</span><span v-else>false</span></p>
  <p>Has player started: <span v-if="hasPlayerStarted">true</span><span v-else>false</span></p>
</template>

<script setup>
import Player from '@vimeo/player';
import { onMounted, ref } from "vue";
const vimeoPlayerContainer = ref(null);
const isPlayerReady = ref(false);
const hasPlayerStarted = ref(false);

onMounted(() => {
  if (vimeoPlayerContainer.value) {
    const player = new Player(vimeoPlayerContainer.value, {
      id: 288344114
    });
    console.log('Initialized player');

    player.ready().then(() => {
      isPlayerReady.value = true;
      console.log('Readied the player');
    });

    player.on('play', function () {
      hasPlayerStarted.value = true;
      console.log('Played the video');
    });
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
