<template>
  <footer class="footer">
    <span class="todo-count">剩余<strong>数量值</strong></span>
    <ul class="filters">
      <li v-for="item in lis" :key="item.id" @click="changeState(item)">
        <a :class="{ selected: item.isSelect }" href="javascript:;">{{
          item.name
        }}</a>
      </li>
    </ul>
    <button class="clear-completed">清除已完成</button>
  </footer>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'
export default {
  data() {
    return {
      lis: [
        {
          id: uuidv4(),
          name: '全部',
          isSelect: true
        },
        {
          id: uuidv4(),
          name: '未完成',
          isSelect: false
        },
        {
          id: uuidv4(),
          name: '已完成',
          isSelect: false
        }
      ]
    }
  },
  methods: {
    changeState(item) {
      // 获取当前的小li对象
      // this.lis.forEach((i) => {
      //   if (i === item) {
      //     i.isSelect = true
      //   } else {
      //     i.isSelect = false
      //   }
      // })

      // 排他思想
      this.lis.forEach((i) => (i.isSelect = i === item))
      this.$emit('change-state', item.name)
    }
  }
}
</script>
