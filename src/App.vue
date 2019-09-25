<template>
  <div id="app">
    <!-- https://www.nasa.gov/rss/dyn/lg_image_of_the_day.rss-->
    <DownloadButton v-on:receive="receiveMessage" rss-url="./static/test.rss">Test1 download</DownloadButton>
    <DownloadButton v-on:receive="receiveMessage" rss-url="./static/test2.rss">Test2 download</DownloadButton>
    <RssList v-bind:rss-data="rssData" v-bind:is-received="isReceived" />
  </div>
</template>

<script>
import DownloadButton from './components/DownloadButton'
import RssList from './components/RssList'

export default {
  name: 'App',
  data() {
    return {
      rssData: null,
      isReceived: false
    }
  },
  components: {
    DownloadButton,
    RssList
  },

  methods: {
    receiveMessage(data) {
      console.log(data)
      this.rssData = data;
      this.isReceived = true;
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
