<template>
  <div id="HelloVue3">
    <p>我是HelloVue3组件-生命周期test</p>
    <input type="text" v-model="message">
    <p>{{message}}</p>
    <div v-pre>
      经测试与vue2对比：
      <table>
        <thead>
          <tr>
            <th>vue2</th>
            <th>vue3</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>beforeCreate</td>
            <td>setup</td>
          </tr>
          <tr>
            <td>created</td>
            <td>setup</td>
          </tr>
          <tr>
            <td>beforeMount</td>
            <td>onBeforeCreat</td>
          </tr>
          <tr>
            <td>mounted</td>
            <td>onMounted</td>
          </tr>
          <tr>
            <td>beforeUpdate</td>
            <td>onBeforeCreated</td>
          </tr>
          <tr>
            <td>updated</td>
            <td>onUpdated</td>
          </tr>
          <tr>
            <td>beforeDestroy</td>
            <td>onBeforeUnmount</td>
          </tr>
          <tr>
            <td>destroyed</td>
            <td>onUnmounted</td>
          </tr>
        </tbody>
      </table>
      <p>
        打开 <b>f12</b> 看生命周期方法运行顺序
      </p>
    </div>
  </div>
</template>

<script>
import { onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue'

export default {
  name: 'HelloVue3',
  components: {},
  
  setup(){
    const message = ""

    // -----------------------------------------------------------------------------
    // 生命周期
    console.log("HelloVue3 setup")
    // 渲染dom之前
    onBeforeMount(_ => {
      console.log("HelloVue3 onBeforeMount")
    })
    // 渲染dom之后
    onMounted(_ => {
      console.log("HelloVue3 onMounted")
    })
    // 数据更新前
    onBeforeUpdate(_ => {
      console.log("HelloVue3 onBeforeUpdate")
    })
    // 数据更新后
    onUpdated(_ => {
      console.log("HelloVue3 onUpdated")
    })
    // 卸载组件前
    onBeforeUnmount(_ => {
      console.log("HelloVue3 onBeforeUnmount")
    })
    // 卸载组件后
    onUnmounted(_ => {
      console.log("HelloVue3 onUnmounted")
    })
    // -----------------------------------------------------------------------------
    
    return { message }
  }
}
</script>

<style>
  table{
    text-align: left;
  }
</style>
