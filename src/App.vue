<template>
  <div>
    <MyHeader></MyHeader>
    <MyMain></MyMain>
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
  }
}
</script>

<style></style>
