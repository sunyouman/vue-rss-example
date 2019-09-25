<template>
  <div>
    <button v-bind:disabled="isButtonDisabled" @click="btClick">
        <slot></slot>
    </button>
  </div>
</template>

<script>

const axios = require('axios');
const convert = require('xml-js');

export default {
    name: 'DownloadButton',
    props: ["rssUrl"],
    data() {
        return {
            isButtonDisabled: false
        }
    },
    methods: {
        btClick() {
            this.isButtonDisabled = true;
            var bt = this;
            axios.get(this.rssUrl).then(response => {
                var json = convert.xml2js(response.data, {compact: true, spaces: 4});
                bt.$emit('receive', json);
            });
        }
    },
}
</script>

<style>

</style>