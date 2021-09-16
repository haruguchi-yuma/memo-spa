<template>
  <div>
    <h2 v-if="mode">一覧</h2>
    <h2 v-else>編集</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mode: true
    }
  }
}
</script>
