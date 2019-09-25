<template>
<div v-if="isReceived">
    <div class="title">{{title}}</div>
    <div class="description">{{description}}</div>
    <div class="row" v-for="item in rssData.rss.channel.item" :key="item.id">
        <img v-bind:src="item.enclosure._attributes.url" class="title-img" />
        <div class="row-text">
        <div class="row-title">{{ item.title._text }}</div>
        <div class="row-description">{{ item.description._text }}</div>
        </div>
    </div>
</div>
<div v-else>
    Please click download button!!
</div>
</template>

<script>
export default {
  props: {'rssData':Object, 'isReceived':Boolean},
  computed: {
      title() {
          return 'RSS title [' + this.rssData.rss.channel.title._text + ']';
      },
      description() {
          return 'RSS Description: ' + this.rssData.rss.channel.description._text;
      }
  },

}
</script>

<style>
.title {
    font-size: 2.8em;
    color: seagreen;
}

.description {
    font-size: 1.7em;
    color: darkgray;
}

.row {
    width: 100%;
    display: inline-flex;
}

.row:nth-child(odd) {
    background-color: aliceblue;
}

.row-text {
    width:80%;
    text-align:left;
    padding: 10px;
}

.row-title {
    color: red;
    font-size: 1.8em;
    font-weight: bold;
}

.row-description {
    color: gray;
    font-size: 1.em;
    margin-top: 10px;
}

.title-img {
    width: 20%;
}
</style>