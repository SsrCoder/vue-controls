<template>
  <div>
    <login-style1></login-style1>
  </div>
</template>
<script lang='ts'>
import { Vue, Prop, Component } from "vue-property-decorator";
import LoginStyle1 from "./components/LoginStyle1.vue";

@Component({
  components: {
    LoginStyle1
  }
})
export default class Login extends Vue {}
</script>

<style lang='stylus' scoped></style>
