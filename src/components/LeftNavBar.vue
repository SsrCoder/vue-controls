<template>
  <div>
    <div v-for="item in navList" :key="item.name">
      <router-link :to="item.route">{{ item.name }}</router-link>
      <!-- <button>{{ item.name }}</button> -->
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  props: {
    navList: {
      type: Array,
      default: () => []
    }
  }
});
</script>

<style lang="stylus" scoped></style>
