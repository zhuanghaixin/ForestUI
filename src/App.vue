<template>
    <div id="app">
        <UIButton :color="color" :titleColor="titleColor"
                @handleButtonClick="sayHello"
                :long="long"
                :xsmall="xsmall"
                :small="small"
                :normal="normal"
                :large="large"
                :xlarge="xlarge"
                :border="border"
                :dashed="dashed"
                :text="text"
                :tile="tile"
                :rounded="rounded"
                :circle="circle"
                  :disabled="disabled"

        >Primary
        </UIButton>
        <div class="btn-group">
            <UIButton class="btn-ctrl" @handleButtonClick="relong">long</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="resize('xsmall')">xsmall</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="resize('small')">small</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="resize('normal')">normal</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="resize('large')">large</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="resize('xlarge')">xlarge</UIButton>
        </div>
        <div class="btn-group">
            <UIButton class="btn-ctrl" @handleButtonClick="reborder('normal')">normal</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="reborder('border')">border</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="reborder('dashed')">dashed</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="reborder('text')">text</UIButton>
        </div>
        <div class="btn-group">
            <UIButton class="btn-ctrl" @handleButtonClick="reradius('normal')">normal</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="reradius('tile')">tile</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="reradius('rounded')">rounded</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="reradius('circle')">circle</UIButton>
        </div>
        <div class="btn-group">
            <UIButton class="btn-ctrl" @handleButtonClick="retintcolor('normal')">normal</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="retintcolor('#5B7FFF')">#5B7FFF</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="retintcolor('#36AB80')">#36AB80</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="retintcolor('#FFAB80')">#FFAB80</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="retintcolor('#FF5600')">#FF5600</UIButton>
        </div>
        <div class="btn-group">
            <UIButton class="btn-ctrl" @handleButtonClick="retitlecolor('normal')">normal</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="retitlecolor('#5B7FFF')">#5B7FFF</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="retitlecolor('#36AB80')">#36AB80</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="retitlecolor('#FFAB80')">#FFAB80</UIButton>
            <UIButton class="btn-ctrl" @handleButtonClick="retitlecolor('#FF5600')">#FF5600</UIButton>
        </div>
       color <span>{{color}}</span><br>
       titleColor <span>{{titleColor}}</span>
        <div class="btn-group">
            <UIButton class="btn-ctrl" @handleButtonClick="disable">disabled</UIButton>

        </div>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from "vue-property-decorator";
    import UIButton from "@/components/UIButton.vue";
    //注册 组件
    @Component({
        components: {
            UIButton
        }
    })
    export default class App extends Vue {
        //长按钮
        private long = false;
        //大小
        private xsmall = false;
        private small = false;
        private normal = false;
        private large = false;
        private xlarge = false;
        //边框
        private border = false;
        private dashed = false;
        private text = false;
        private radius = false;
        //圆角
        private tile=false;
        private rounded=false
        private circle=false
        //按钮颜色
        private color=''
        // 标题颜色
        private titleColor=''
        //禁用
        private disabled=false
        //按钮阴影

        //重置大小
        private resize(name: string) {
            //让所有按钮恢复到初始状态


            this.xsmall = false;
            this.small = false;
            this.normal = false;
            this.large = false;
            this.xlarge = false;
            switch (name) {
                case "xsmall":
                    this.xsmall = true;
                    break;
                case "small":
                    this.small = true;
                    break;
                case "normal":
                    this.normal = true;
                    break;
                case "large":
                    this.large = true;
                    break;
                case "xlarge":
                    this.xlarge = true;
                    break;
            }
        }
        //重置长度
        private relong() {
            this.long = !this.long;
        }
        //重置边框
        private reborder(name: string) {
            //让所有按钮恢复到初始状态
            this.normal=false
            this.border = false;
            this.dashed = false;
            this.text = false;
            switch (name) {
                case "border":
                    this.border = true;
                    break;
                case "dashed":
                    this.border = true;
                    this.dashed = true;
                    break;
                case "text":
                    this.text = true;
                    break;
                case "normal":
                    this.normal = true;
                    break;
            }
        }
        //重置圆角
        private reradius(name: string) {
            //让所有按钮恢复到初始状态
            this.normal=false
            this.tile = false;
            this.rounded = false;
            this.circle = false;
            switch (name) {
                case "tile":
                    this.tile = true;
                    break;
                case "rounded":
                    this.rounded = true;
                    break;
                case "circle":
                    this.circle = true;
                    break;
                case "normal":
                    this.normal = true;
                    break;
            }
        }
        //重置按钮颜色
        private retintcolor(name: string){
            if(name==='normal'){
                this.color='#2D8CF0'
            }else{
                this.color=name
            }

        }

        // 重置标题颜色
        private retitlecolor(name: string){
            if(name==='normal'){
                this.titleColor='#000'
            }else{
                this.titleColor=name
            }

        }
        //禁用
        private disable(){
            this.disabled = !this.disabled;
        }
        //重置按钮阴影

        sayHello(e: MouseEvent) {
            console.log(e);
        }
    }
</script>

<style lang="stylus">
    html, body {
        box-sizing: border-box;
        font-size: 18px;
        color: #000;
        font-family: 'Helvetica Neue', Helvetica, Arial, 'Microsoft Yahei', 'Hiragino Sans GB', 'Heiti SC', 'WenQuanYi Micro Hei', sans-serif;
    }

    *, ::before, ::after {
        box-sizing: inherit;
        font-size: inherit;
        font-family: inherit;
        color: inherit;
        font-size: 0.875rem;
        font-weight: 500;
        letter-spacing: 0.09em;
    }

    .btn-group {
        margin: 6px auto;

    }

    .btn-ctrl {
        margin: 0 4px;
    }
</style>
