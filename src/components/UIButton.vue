<template>
  <button
    class="ui-btn"
    @click="onClickBtn"
    :class="{
    'ui-btn-long':long,
    'ui-btn-xsmall':xsmall,
    'ui-btn-small':small,
    'ui-btn-normal':normal,
    'ui-btn-large':large,
    'ui-btn-xlarge':xlarge,
    'ui-btn-border':border,
    'ui-btn-dashed':dashed,
    'ui-btn-text':text,
    'ui-btn-tile':tile,
    'ui-btn-rounded':rounded,
    'ui-btn-circle':circle


  }
    "
  >
    <slot>Button</slot>
  </button>
</template>

<script lang="ts">
import { Vue, Component, Emit, Prop } from "vue-property-decorator";
@Component
export default class UIButton extends Vue {
  // onClickBtn(e: MouseEvent) {
  //   this.$emit("handleButton",e);
  // }

  @Emit("handleButtonClick")
  onClickBtn(e: MouseEvent) {
    return;
  }
  //长按钮
  @Prop(Boolean) readonly long!: boolean;
  //大小
  @Prop(Boolean) readonly xsmall!: boolean;
  @Prop(Boolean) readonly small!: boolean;
  @Prop(Boolean) readonly normal!: boolean;
  @Prop(Boolean) readonly large!: boolean;
  @Prop(Boolean) readonly xlarge!: boolean;
  //边框
  @Prop(Boolean) readonly border!: boolean;
  @Prop(Boolean) readonly dashed!: boolean;
  @Prop(Boolean) readonly text!: boolean;
  //圆角
  @Prop(Boolean) readonly tile!: boolean;
  @Prop(Boolean) readonly rounded!: boolean;
  @Prop(Boolean) readonly circle!: boolean;
  //按钮颜色
  //标题颜色
  //按钮阴影
}
</script>

<style lang="stylus" scoped>
Resize(mW, h, pLR, fs) {
  min-width: mW;
  height: h;
  padding: 0 pLR;
  font-size: fs;
   &.ui-btn-circle{
    width: @height;
     min-width:0px;
     padding:0px;
  }
}

.ui-btn {
  Resize(64px, 36px, 16px, 0.875rem);
  border: 0 solid black;
  background-color: #5d3eff;
  cursor: pointer;
  user-select: none;
  outline: none;

  &:hover {
    background-color: #5234eb;
  }
}

.ui-btn-long {
  width: 100%;
}

.ui-btn-xsmall {
  Resize(36px, 20px, 9px, 0.625rem);
}

.ui-btn-small {
  Resize(50px, 20px, 12px, 0.75rem);
}

.ui-btn-normal {
  Resize(64px, 36px, 16px, 0.875rem);
}

.ui-btn-large {
  Resize(78px, 44px, 19px, 0.875rem);
}

.ui-btn-xlarge {
  Resize(92px, 52px, 23px, 1rem);
}

// 边框
.ui-btn-border {
  border-width: 1px;
  color: black;
}

.ui-btn-dashed {
  border-style: dashed;
}

.ui-btn-text, .ui-btn-border {
  background-color: transparent;
  color: black;
}
//圆角
.ui-btn-tile
  border-radius 0
.ui-btn-rounded,.ui-btn-circle
  border-radius 1000px

</style>
