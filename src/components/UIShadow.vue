<template>
<div></div>
</template>

<script lang="ts">
    import { Vue, Component, Emit, Prop } from "vue-property-decorator";
    @Component
    export default class UIShadow extends Vue {
        //按钮阴影
        @Prop([String,Number]) readonly shadow!: string|number
        protected get Shadow(){
            console.log(this.shadow)
            if(this.shadow){
                return `ui-shadow-${this.shadow}`
            }
            return 'ui-shadow-0'
        }

    }
</script>
<style lang="stylus">
    Shadow(a, b, c)
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
        Shadow(11px 15px -7px, 24px 38px 3px, 9px 46px 8px)
</style>

