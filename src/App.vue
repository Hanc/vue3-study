<template>
  <h2>reactive和ref的细节问题</h2>
  <h1>m1:{{m1}}</h1>
  <h1>m2:{{m2}}</h1>
  <h1>m3:{{m3}}</h1>
  <hr>
  <button @click="update">更新数据</button>
</template>

<script lang="ts">
import { defineComponent, ref, reactive } from 'vue';

// defineComponent函数,目的是定义一个组件，内部可以传入一个配置对象
export default defineComponent({
  name: 'App',
  setup() {
    const m1 = ref('abc');
    const m2 = reactive({
      name: '路飞',
      friends :{
        name: '索隆ls'
      }
    });
    const m3 = ref({
      name: '路飞',
      friends :{
        name: '索隆ls'
      }
    });
    const update = () =>{
      m1.value += '==='
      m2.friends.name = '乔巴'
      m3.value.name = '娜美'
    }
    return {
      m1, m2, m3, update
    }
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
