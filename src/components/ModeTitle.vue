<template>
  <div>
    <h2 v-if="!editMode">一覧</h2>
    <h2 v-else>編集</h2>
  </div>
</template>

<script>
export default {
  props: {
    'editMode': Boolean,
  }
}
</script>
