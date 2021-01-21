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

        const show1 = ()=>{
            console.log('setup-show1');
        }
        return{
            show1
        }
    },

    data() {
        return {
            count : 1,
        }
    },

    //界面渲染后的生命周期回调
    mounted() {
        console.log(this);
    },

    methods: {
        show(){
            console.log('method-show');
        }
    },
})
</script>
<style lang="">
    
</style>