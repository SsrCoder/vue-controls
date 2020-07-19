<template>
  <div>
    <a class="streamer_btn" href="javascript:;" :style="buttonTextStyle()">{{
      text
    }}</a>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";

@Component
export default class StreamerButton extends Vue {
  @Prop(String)
  private text = "流光特效";

  @Prop(Number)
  private textSize = 24;

  @Prop(String)
  private textColor = "#FFFFFF";

  @Prop(Number)
  private borderRadius = -1;
  @Prop(Array)
  private backgroundColors = ["#03A9F4", "#F441A5", "#FFEB3B", "#03A9F4"];

  @Prop(Number)
  private width = 400;

  @Prop(Number)
  private height = 100;

  buttonTextStyle(): object {
    const bgColor = this.backgroundColors.join(",");
    const borderRadius =
      this.borderRadius >= 0
        ? this.borderRadius
        : this.width >= this.height
        ? this.height / 2
        : this.width / 2;

    return {
      "--text-size": this.textSize + "px",
      "--background": `linear-gradient(90deg, ${bgColor})`,
      "--width": this.width + "px",
      "--height": this.height + "px",
      "--text-color": this.textColor,
      "--border-radius": borderRadius + "px"
    };
  }
}
</script>

<style lang="stylus" scoped>
.streamer_btn
  position absolute
  color var(textColor)
  text-decoration none
  font-size var(--text-size)
  background var(--background)
  background-size 400%
  width var(--width)
  height var(--height)
  line-height var(--height)
  text-align center
  border-radius var(--border-radius)

.streamer_btn:hover
  animation sun 8s infinite

.streamer_btn::before
  content ''
  position absolute
  left -5px
  right -5px
  top -5px
  bottom -5px
  border 1px solid red
  background var(--background)
  background-size 400%
  border-radius var(--border-radius)
  filter blur(20px)
  z-index -1

.streamer_btn:hover::before
  animation sun 8s infinite

@keyframes sun
  100%
    background-position -400% 0
</style>
