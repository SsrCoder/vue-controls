<template>
  <div>
    <div class="container" @mouseenter="mouseEnter" @mouseleave="mouseLeave">
      <h1>bilibili</h1>
      <form action="" method="post">
        <input type="text" class="tbx" placeholder="username" />
        <input type="password" class="tbx" placeholder="password" />
        <input type="submit" class="sub" value="登录" />
      </form>
      <span ref="span"></span>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Prop, Component } from "vue-property-decorator";

@Component
export default class LoginStyle1 extends Vue {
  @Prop(String)
  title = "Login Style1";

  canIn = true;
  canOut = false;

  mouseEnter(event: MouseEvent) {
    if (this.canIn) {
      const target = event.target as HTMLElement;

      const x = event.clientX - target.offsetLeft,
        y = event.clientY - target.offsetTop;

      const span = this.$refs.span as HTMLElement;
      span.style.left = x + "px";
      span.style.top = y + "px";
      span.classList.add("in");
      span.classList.remove("out");
      this.canIn = false;
      this.canOut = true;
    }
  }

  mouseLeave(event: MouseEvent) {
    if (this.canOut) {
      const target = event.target as HTMLElement;

      const x = event.clientX - target.offsetLeft,
        y = event.clientY - target.offsetTop;

      const span = this.$refs.span as HTMLElement;
      span.style.left = x + "px";
      span.style.top = y + "px";
      span.classList.add("out");
      span.classList.remove("in");
      this.canIn = true;
      this.canOut = false;
    }
  }
}
</script>

<style lang="stylus" scoped>
.container
  display flex
  justify-content center
  align-items center
  flex-direction column
  width 300px
  height 450px
  border-radius 20px
  background-color #34495e
  box-shadow 15px 15px 10px rgba(33, 45, 58, 0.3)
  overflow hidden
  position relative

  form
    width 400px
    height 200px
    display flex
    justify-content space-around
    flex-direction column
    align-items center
    z-index 1

    .tbx
      width 200px
      height 40px
      outline none
      border none
      border-bottom 1px solid #fff
      background none
      color #ffffff

      ::placeholder
        color #fff
        font-size 15px

    .sub
      width 200px
      height 40px
      outline none
      border 1px solid #fff
      border-radius 20px
      letter-spacing 5px
      color #fff
      background none
      cursor pointer

  h1
    z-index 1
    color #ecf0f1
    letter-spacing 5px
    padding-left 5px
    font-size 50px
    font-weight 100
    text-shadow 5px 5px 5px rgba(33, 45, 58, 0.3)

  .in
    position absolute
    top 0
    left 0
    display block
    width 0
    height 0
    border-radius 50%
    background #3498BD
    transform translate(-50%, -50%)
    animation inAnimation 0.8s ease-out forwards

  .out
    position absolute
    top 0
    left 0
    display block
    width 1200
    height 1200
    border-radius 50%
    background #3498BD
    transform translate(-50%, -50%)
    animation outAnimation 0.8s ease-out forwards

@keyframes inAnimation
  0%
    width 0
    height 0

  100%
    width 1200px
    height 1200px

@keyframes outAnimation
  0%
    width 1200px
    height 1200px

  100%
    width 0
    height 0
</style>
