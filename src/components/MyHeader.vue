<template>
  <header class="header">
    <h1>todos</h1>
    <input id="toggle-all" class="toggle-all" type="checkbox" v-model="isAll" />
    <label for="toggle-all"></label>
    <input
      v-model="task"
      class="new-todo"
      placeholder="输入任务名称-回车确认"
      autofocus
      @keydown.enter="addtodo"
    />
  </header>
</template>

<script>
// 引入唯一id
import { v4 as uuidv4 } from 'uuid'
export default {
  props: ['list'],
  data() {
    return {
      task: ''
    }
  },
  methods: {
    addtodo() {
      // 判断输入框有无内容
      if (this.task.trim() === '') {
        alert('请输入正确的任务名')
        this.task = ''
        return
      }
      const add = {
        id: uuidv4(),
        name: this.task,
        isDone: false
      }
      //   添加
      this.list.push(add)

      // 输入成功后，清空输入框
      this.task = ''
    }
  },
  computed: {
    isAll: {
      get() {
        return this.list.every((item) => item.isDone)
      },
      set(newChecked) {
        this.list.forEach((item) => {
          item.isDone = newChecked
        })
      }
    }
  }
}
</script>
