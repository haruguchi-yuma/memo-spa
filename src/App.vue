<template>
  <div id="app">
    <MemoHeader></MemoHeader>
    <ModeTitle :edit-mode="editMode"></ModeTitle>
    <div class="container">
      <div class="memo-list">
        <ul v-for="memo in memos" :key="memo.id">
          <li
            style="display: inline;"
            @click="editable(memo)"
          >
              {{memo.body | firstLine}}
          </li>
        </ul>
        <p>編集モード:{{ editMode }}</p>
        <button>+</button>
      </div>
      <div class="edit">
        <EditFrom v-show="editMode" :edit-body="memoBody"></EditFrom>
      </div>
    </div>
  </div>
</template>

<script>
import MemoHeader from './components/MemoHeader.vue'
import ModeTitle from './components/ModeTitle.vue'
import EditFrom from './components/EditFrom.vue'

export default {
  name: 'App',
  components: {
    MemoHeader,
    ModeTitle,
    EditFrom
  },
  data() {
    return {
      editMode: false,
      memoBody: '',
      memos: [
        {id: 1, body: `今日すること\n買い物\n買い出し\nご飯食べる`},
        {id: 2, body: '今月の目標\n地域rbに参加\nメモアプリの完成'},
        {id: 3, body: '最近ハマっていること\nGitの学習\nhogehoge'}
      ]
    }
  },
  methods: {
    editable(memo) {
      this.editMode = !this.editMode
      this.memoBody = memo.body
    }
  },
  filters: {
    firstLine(value) {
      return value.split(/\r\n|\r|\n/)[0]
    }
  }
}
</script>

<style scoped>
#app {
  width: 80%;
  margin: 0 auto;
}

.edit {
  width: 50%;
}

.container {
  width: 100%;
  border: 1px solid gray;
  display: flex;
  justify-content: space-between;
}

ul {
  padding-left: 20px;
}
</style>
