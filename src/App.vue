<template>
  <div id="app">
    <left-nav-bar :navList="navList"></left-nav-bar>
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
    <router-view />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import LeftNavBar from "@/components/LeftNavBar.vue";

export default Vue.extend({
  components: {
    LeftNavBar
  },
  data() {
    return {
      navList: [
        {
          name: "主页",
          route: "/"
        },
        {
          name: "按钮",
          route: "/button"
        },
        {
          name: "登录",
          route: "/login"
        }
      ]
    };
  }
});
</script>

<style lang="stylus">
*
  margin 0
  padding 0

#app
  font-family Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  // text-align center
  color #2c3e50
  // margin-top 60px
</style>
