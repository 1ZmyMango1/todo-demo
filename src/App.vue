<template>
  <div>
    <MyHeader :list="list"></MyHeader>
    <MyMain :list="list" @del-todo="delTode"></MyMain>
    <MyFooter></MyFooter>
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
      list: [
        { id: 100, name: '吃饭', isDone: true },
        { id: 201, name: '睡觉', isDone: false },
        { id: 103, name: '打豆豆', isDone: true }
      ]
    }
  },
  methods: {
    // 删除
    delTode() {
      console.log('父组件正在删除')
    }
  }
}
</script>

<style></style>
