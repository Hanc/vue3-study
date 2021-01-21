<template>
    <h2>Child子组件</h2>
    <h3>{{msg}}</h3>
</template>
<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
    name: 'Child',
    props: ['msg'],
    //数据初始化的生命周期回调
    beforeCreate() {
        console.log('beforeCreate执行了-2');
        
    },
    setup() {
        //this是undefined
        console.log('setup执行了-1', this);
        return{

        }
    }
})
</script>
<style lang="">
    
</style>