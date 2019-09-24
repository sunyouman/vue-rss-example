<template>
  <div id="app">
    <DownloadButton v-on:receive="receiveMessage"/>
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
