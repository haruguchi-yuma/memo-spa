<template>
  <div class="edit-form">
    <textarea cols="40" rows="20" v-model="editBody" v-memo-focus="editMode"></textarea>
    <button @click="edit()">編集</button>
    <button @click="destroy(editId)">削除</button>
  </div>
</template>

<script>
export default {
  props: ['editId', 'editBody', 'editMode'],
  methods: {
    destroy(Id) {
      this.$emit('delete-memo-id', Id)
    },
    edit() {
      this.$emit('edit-memo', {
        editId: this.editId,
        editBody: this.editBody
      })
    }
  },
  directives: {
    "memo-focus": function(el, binding) {
      if (binding.value) {
        el.focus();
      }
    }
  },
}
</script>


<style scoped>
.edit-form {
  margin: 0 auto;
  color: #333;
}
textarea {
  margin-top: 15px;
  margin-bottom: 10px;
  display: block;
}
button {
  margin-left: 5px;
  padding: 0.3rem 2rem;
  border-radius: 10px;
  border-color: #ccc;
  background: #eee;
}
</style>
