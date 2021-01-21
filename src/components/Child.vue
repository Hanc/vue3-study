<template>
    <h2>Child子组件</h2>
    <h3>{{msg}}</h3>
    <button @click="emitChange">分发事件</button>
</template>
<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
    name: 'Child',
    props: ['msg'],
    //数据初始化的生命周期回调
    setup(props, context) {
        //this是undefined
        console.log(props);
        console.log(context);
        console.log(context.attrs);
        console.log(context.attrs.msg2);
        console.log(context.emit);
        console.log(context.slots);


        function emitChange() {
            context.emit('change', '++')
        }
        const show1 = ()=>{
            console.log('setup-show1');
        }
        return{
            show1, emitChange
        }
    },
})
</script>
<style lang="">
    
</style>