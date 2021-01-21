<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h3>名字：{{user.name}}</h3>
  <h3>年龄：{{user.age}}</h3>
  <h3>性别：{{user.gender}}</h3>
  <h3>朋友：{{user.friends}}</h3>
  <button @click="update()">更新数据</button>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

// defineComponent函数,目的是定义一个组件，内部可以传入一个配置对象
export default defineComponent({
  name: 'App',
  setup(){
    const obj = {
      name: '张三',
      age: 20,
      friends :{
        name : '李四',
        age : '18',
        friends: ['王五', '赵四'],
      },
    }

    //返回的是一个Proxy的代理对象，被代理的目标对象就是obj对象
    const user = reactive<any>(obj);

    console.log(user);

    const update = () =>{
      // user.name = '王五',
      // user.age += 2,
      // user.friends.friends[0] = '张三'
      delete user.age
    }
    return {
      user,update
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
