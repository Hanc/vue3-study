<template>
  <h2 class="mb-4">计算属性和监视</h2>
  <div class="container mx-auto py-2 px-4 bg-gray-300 flex flex-col">
    <fieldset class="py-2">
    <legend class="text-2xl">姓名和操作</legend>
    姓氏：<input type="text" class="px-4 py-2 mb-2" placeholder="请输入姓氏" v-model="user.firstName"/>

    名字：<input type="text" class="px-4 py-2 mb-2" placeholder="请输入名字" v-model="user.lastName"/>
  </fieldset>
      <fieldset class="py-2">
    <legend class="text-2xl">姓名和操作</legend>
    <label for="">姓氏：</label><input type="text" class="px-4 py-2 mb-2" placeholder="显示姓名" v-model="fullName1"/>
 
    名字：<input type="text" class="px-4 py-2 mb-2" placeholder="显示姓名" v-model="fullName2"/>

  </fieldset>
  <div>
    名字：<input type="text" class="px-4 py-2 mb-2" placeholder="显示姓名" v-model="fullName3"/>
  </div>
  </div>
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
