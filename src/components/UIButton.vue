<template>
  <button
    class="ui-btn"
    @click="onClickBtn"
    :class="[Shadow,{
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
    'ui-btn-circle':circle,
    'ui-btn-disabled':disabled

  }]
    "
    :style="{
      '--color-tint':TintColor,
      '--color-title':TitleColor
    }"
  >
    <slot>Button</slot>
  </button>
</template>

<script lang="ts">
import { Vue, Component, Emit, Prop,Mixins} from "vue-property-decorator";
import UIShadow from './UIShadow.vue';
@Component
export default class UIButton extends Mixins(UIShadow) {
  // onClickBtn(e: MouseEvent) {
  //   this.$emit("handleButton",e);
  // }
  //发送点击事件
  @Emit("handleButtonClick")
  emitClick(e: MouseEvent) {
    return;
  }
  private onClickBtn(e: MouseEvent) {
    if (!this.disabled) {
      this.emitClick(e);
    }
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
  @Prop(String) readonly color!: string;
  //标题颜色
  @Prop(String) readonly titleColor!: string;
  //禁用状态
  @Prop(Boolean) readonly disabled!: boolean;
  // //按钮阴影
  // @Prop([String,Number]) readonly shadow!: string|number
  // private get Shadow(){
  //   console.log(this.shadow)
  //   if(this.shadow){
  //     return `ui-shadow-${this.shadow}`
  //   }
  //   return 'ui-shadow-0'
  // }
  //颜色可能是undefined，所以用计算属性
  private get TintColor() {
    if (this.disabled) {
      if (this.border || this.text) {
        return "#C5C8CE";
      }
      return "#f5f5f5";
    }
    if (this.color) {
      return this.color;
    }
    return "#2D8CF0";
  }
  //颜色可能是undefined，所以用计算属性
  private get TitleColor() {
    if (this.disabled) {
      return "#C5C8CE";
    }
    if (this.titleColor) {
      return this.titleColor;
    }
    if (this.border || this.text) {
      return this.TintColor;
    }
    return "#000";
  }



  private get msg() {
    return 14;
  }
}
</script>

<style lang="stylus" scoped>
Resize(mW, h, pLR, fs) {
  min-width: mW;
  height: h;
  padding: 0 pLR;
  font-size: fs;

  &.ui-btn-circle {
    width: @height;
    min-width: 0px;
    padding: 0px;
  }
}

.ui-btn {
  Resize(64px, 36px, 16px, 0.875rem);
  border: 0 solid var(--color-tint);
  /* background-color: #5b7fff; */
  background-color: var(--color-tint);
  cursor: pointer;
  user-select: none;
  outline: none;
  color: var(--color-title);

  &:not(.ui-btn-disabled):hover {
    filter:brightness(120%)
  }
  &:active{
    filter:brightness(80%)

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
}

.ui-btn-dashed {
  border-style: dashed;
}

.ui-btn-text, .ui-btn-border {
  background-color: transparent;
}

// 圆角
.ui-btn-tile {
  border-radius: 0;
}

.ui-btn-rounded, .ui-btn-circle {
  border-radius: 1000px;
}

// 禁用
.ui-btn-disabled {
  cursor: not-allowed;
}
//阴影
/*Shadow(a, b, c)
  box-shadow 0 a rgba(0, 0, 0, 0.2), 0 b rgba(0, 0, 0, 0.14), 0 c rgba(0, 0, 0, 0.12)
.ui-shadow-1
  Shadow(2px 1px -1px, 1px 1px 0, 1px 3px 0)
.ui-shadow-2
  Shadow(3px 1px -2px, 2px 2px 0, 1px 5px 0)
.ui-shadow-3
  Shadow(3px 3px -2px, 3px 4px 0, 1px 8px 0)
.ui-shadow-4
  Shadow(2px 4px -1px, 4px 5px 0, 1px 10px 0)
.ui-shadow-5
  Shadow(3px 5px -1px, 5px 8px 0, 1px 14px 0)
.ui-shadow-6
  Shadow(3px 5px -1px, 6px 10px 0, 1px 18px 0)
.ui-shadow-7
  Shadow(4px 5px -2px, 7px 10px 1px, 2px 16px 1px)
.ui-shadow-8
  Shadow(5px 5px -3px, 8px 10px 1px, 3px 14px 2px)
.ui-shadow-9
  Shadow(5px 6px -3px, 9px 12px 1px, 3px 16px 2px)
.ui-shadow-10
  Shadow(6px 6px -3px, 10px 14px 1px, 4px 18px 3px)
.ui-shadow-11
  Shadow(6px 7px -4px, 11px 15px 1px, 4px 20px 3px)
.ui-shadow-12
  Shadow(7px 8px -4px, 12px 17px 2px, 5px 22px 4px)
.ui-shadow-13
  Shadow(7px 8px -4px, 13px 19px 2px, 5px 24px 4px)
.ui-shadow-14
  Shadow(7px 9px -4px, 14px 21px 2px, 5px 26px 4px)
.ui-shadow-15
  Shadow(8px 9px -5px, 15px 22px 2px, 6px 28px 5px)
.ui-shadow-16
  Shadow(8px 10px -5px, 16px 24px 2px, 6px 30px 5px)
.ui-shadow-17
  Shadow(8px 11px -5px, 17px 26px 2px, 6px 32px 5px)
.ui-shadow-18
  Shadow(9px 11px -5px, 18px 28px 2px, 7px 34px 6px)
.ui-shadow-19
  Shadow(9px 12px -6px, 19px 29px 2px, 7px 36px 6px)
.ui-shadow-20
  Shadow(10px 13px -6px, 20px 31px 3px, 8px 38px 7px)
.ui-shadow-21
  Shadow(10px 13px -6px, 21px 33px 3px, 8px 40px 7px)
.ui-shadow-22
  Shadow(10px 14px -6px, 22px 35px 3px, 8px 42px 7px)
.ui-shadow-23
  Shadow(11px 14px -7px, 23px 36px 3px, 9px 44px 8px)
.ui-shadow-24
  Shadow(11px 15px -7px, 24px 38px 3px, 9px 46px 8px)*/
</style>
