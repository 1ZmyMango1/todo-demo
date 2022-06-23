<template>
  <ul class="todo-list">
    <!-- completed: 完成的类名 -->
    <li
      :class="{ completed: item.isDone }"
      v-for="item in fileteredList"
      :key="item.id"
    >
      <div class="view">
        <input class="toggle" type="checkbox" v-model="item.isDone" />
        <label>{{ item.name }}</label>
        <button class="destroy" @click="delTodo(item.id)"></button>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  props: ['list', 'currentState'],
  data() {
    return {}
  },
  methods: {
    delTodo(id) {
      // 通知父组件删除数据
      this.$emit('del-todo', id)
    }
  },
  computed: {
    fileteredList() {
      switch (this.currentState) {
        case '全部':
          return this.list
        case '未完成':
          return this.list.filter((item) => !item.isDone)
        case '已完成':
          return this.list.filter((item) => item.isDone)
        default:
          return []
      }
    }
  }
}
</script>
