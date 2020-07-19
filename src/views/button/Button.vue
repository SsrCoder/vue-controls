<template>
  <div>
    <streamer-button></streamer-button>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import StreamerButton from "./components/StreamerButton.vue";

export default Vue.extend({
  components: {
    StreamerButton
  }
});
</script>

<style lang="stylus" scoped></style>
