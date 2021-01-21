<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h3>{{msg}}</h3>
  <button @click="msg += '==='">更新</button>
  <hr>
  <Child :msg="msg" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Child from './components/Child.vue'

// defineComponent函数,目的是定义一个组件，内部可以传入一个配置对象
export default defineComponent({
  name: 'App',
  components: {
    Child
  },
  setup() {
    const msg = ref('Hello vue');
    return {
      msg
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
