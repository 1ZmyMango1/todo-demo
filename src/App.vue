<template>
  <!-- @del-todo="delTode = list = list.filter((item) => item.id !== $event) -->
  <div>
    <MyHeader :list="list"></MyHeader>
    <MyMain
      :list="list"
      @del-todo="delTode"
      :currentState="currentState"
    ></MyMain>
    <MyFooter
      @del-done="delDone"
      @change-state="currentState = $event"
    ></MyFooter>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue'
import MyFooter from './components/MyFooter.vue'
export default {
  components: {
    MyHeader,
    MyMain,
    MyFooter
  },
  data() {
    return {
      currentState: '全部',
      list: [
        { id: 100, name: '吃饭', isDone: true },
        { id: 201, name: '睡觉', isDone: false },
        { id: 103, name: '打豆豆', isDone: true }
      ]
    }
  },
  methods: {
    // 删除
    delTode(id) {
      // console.log('父组件正在删除')
      this.list = this.list.filter((item) => item.id !== id)
      // this.list.splice(index, 1)
    },
    // 清除已完成
    delDone() {
      this.list = this.list.filter((item) => !item.isDone)
    }
  }
}
</script>

<style></style>
