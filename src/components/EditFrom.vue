<template>
  <div class="edit-form">
    <textarea cols="40" rows="10" v-model="editBody"></textarea>
    <button>編集</button>
    <button>削除</button>
    <p>{{ editBody }}</p>
  </div>
</template>

<script>
export default {
  props: {
    'editBody': String
  }
}
</script>


<style scoped>
.edit-form {
  margin: 0 auto;
}
textarea {
  display: block;
}
</style>
