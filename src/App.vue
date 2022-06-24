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
      :list="list"
      @del-done="delDone"
      @change-state="currentState = $event"
    ></MyFooter>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue'
import MyFooter from './components/MyFooter.vue'

const TODOLIST = 'TODO-LIST'
export default {
  components: {
    MyHeader,
    MyMain,
    MyFooter
  },
  data() {
    return {
      currentState: '全部',
      list: JSON.parse(localStorage.getItem(TODOLIST)) || []
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
  },
  watch: {
    list: {
      // 深度监听
      deep: true,
      // 打开页面自动监听
      immediate: true,
      handler(newList) {
        localStorage.setItem(TODOLIST, JSON.stringify(newList))
      }
    }
  }
}
</script>

<style></style>
