<template>
  <div id="app">
    <MemoHeader></MemoHeader>
  </div>
</template>

<script>
import MemoHeader from './components/MemoHeader.vue'

export default {
  name: 'App',
  components: {
    MemoHeader
  }
}
</script>

<style scoped>
#app {
  width: 80%;
  margin: 0 auto;
}
</style>
