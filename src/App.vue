<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div>{{count}}</div>
  <button @click="update()">+1</button>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

// defineComponent函数,目的是定义一个组件，内部可以传入一个配置对象
export default defineComponent({
  name: 'App',
  setup(){
    const count = ref(1);
    console.log(count);
    function update() {
      count.value++;
    }
    return {
      count,update
    };
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
