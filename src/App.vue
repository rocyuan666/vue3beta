<template>
  <div id="app">
    <button @click="changeMessage">改变内容</button>
    <h1>{{data1.message}}</h1>
    <!-- 计算属性两种用法 -->
    <p>{{computeFn}}</p>
    <p>{{data1.numberCompute}}</p>

    <button @click="isRemove">移除/添加</button>
    <hello-vue3 v-if="data1.isShow"></hello-vue3>
  </div>
</template>

<script>
import helloVue3 from "./components/HelloVue3"
import { reactive, computed } from 'vue'

export default {
  name: 'App',
  components: {
    helloVue3
  },
  setup(){
    // 1.生命周期方法，见 helloVue3 组件
    /**
     * setup
     * onBeforeMount
     * onMounted
     * onBeforeUpdate
     * onUpdated
     * onBeforeUnmount
     * onUnmounted
     */

    // 2.reactive API - 定义数据
    // 相比于vue2中data定义，data中数据多了后容易混淆，想要知道变量对应哪些数据比较困难，vue3中以这种方式可以将数据归类，一眼就知道了，你品，仔细品
    const data1 = reactive({
      message: "我是Vue3.0beta-message",
      number: 2,
      numberCompute: computed(_ => data1.number * data1.number),
      isShow: true
    })
    //更改不了,需要reactiv定义数据----下面错误做法-----
    // const message = "我是Vue3.0beta"
    // let isShow = true
    // const isRemove = _ => {
    //   isShow = !.isShow
    // }

    // 3.定义事件处理方法
    const isRemove = _ => {
      data1.isShow = !data1.isShow
    }
    // 修改 message 值
    const changeMessage = _ => {
      data1.message = "我是Vue3.0beta-改变后的message"
    }

    // 4.计算属性-两种写法，也可定义在 reactive 中 见 reactive 
    const computeFn = computed(_ => {
      return data1.number * data1.number
    })

    return { data1, isRemove, changeMessage, computeFn}
  }
}
</script>

<style>

</style>
