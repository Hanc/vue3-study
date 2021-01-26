<template>
  <h2>计算属性和监视</h2>
  <fieldset>
    <legend>姓名和操作</legend>
    姓氏：<input type="text" placeholder="请输入姓氏" v-model="user.firstName"/>
    <br />
    名字：<input type="text" placeholder="请输入名字" v-model="user.lastName"/>
  </fieldset>
  <fieldset>
    <legend>计算属性和监视的演示</legend>
    <legend>姓名和操作</legend>
    姓氏：<input type="text" placeholder="显示姓名" v-model="fullName1"/>
    <br />
    名字：<input type="text" placeholder="显示姓名" v-model="fullName2"/>
      <br />
    名字：<input type="text" placeholder="显示姓名" v-model="fullName3"/>
  </fieldset>
</template>

<script lang="ts">
import { defineComponent, reactive, computed, watch, ref, watchEffect } from 'vue';

// defineComponent函数,目的是定义一个组件，内部可以传入一个配置对象
export default defineComponent({
  name: 'App',
  setup() {
    const user = reactive({
      firstName : '东方',
      lastName : '不败'
    })

    //返回ref类型对象
    const fullName1 = computed(()=>{
      return user.firstName + '_' +user.lastName
    })

    //set和get
    const fullName2 = computed({
      get(){
        return user.firstName + '_' +user.lastName
      },
      set(val: string){
        const names = val.split('_')
        user.firstName = names[0]
        user.lastName = names[1]
      }
    })

    // 监视指定的数据
    const fullName3 = ref('')
    watch(user, ({firstName, lastName}) =>{
      fullName3.value = firstName+ '_'+ lastName
    },{immediate:true, deep:true})

    watchEffect(() =>{
      const names1 = fullName3.value.split('_');
        // const names = fullName3.value.split('_')
        user.firstName = names1[0]
        user.lastName = names1[1]
    })

    return {
      user, fullName1, fullName2, fullName3
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
