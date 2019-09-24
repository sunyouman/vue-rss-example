<template>
  <div>
    <button v-bind:disabled="isButtonDisabled" @click="btClick">{{buttonText}}</button>
  </div>
</template>

<script>

const axios = require('axios');
const convert = require('xml-js');
const request = require('request');

export default {
    name: 'DownloadButton',
    data() {
        return {
            isButtonDisabled: false,
            buttonText: 'Download'
        }
    },
    methods: {
        btClick() {
            this.isButtonDisabled = true;
            this.buttonText = 'Received';
            var bt = this;
            // https://www.nasa.gov/rss/dyn/lg_image_of_the_day.rss
            axios.get('./static/test.rss').then(response => {
                var json = convert.xml2js(response.data, {compact: true, spaces: 4});
                bt.$emit('receive', json);
            });
        }
    },
}
</script>

<style>

</style>