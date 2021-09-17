<template>
  <div class="edit-form">
    <textarea cols="40" rows="10" v-model="editBody"></textarea>
    <button>編集</button>
    <button @click="destroy(editId)">削除</button>
    <p>id: {{ editId }}, body: {{ editBody }}</p>
  </div>
</template>

<script>
export default {
  props: ['editId', 'editBody'],
  methods: {
    destroy(Id) {
      this.$emit('delete-memo-id', Id)
    }
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
