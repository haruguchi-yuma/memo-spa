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
              <a href="#">{{memo.body | firstLine}}</a>
          </li>
        </ul>
        <p>編集モード:{{ editMode }}</p> <!-- デバッグ用 -->
        <p><a href="#" @click="creatable()">+</a></p>
      </div>
      <div class="edit">
        <EditFrom v-show="editMode" :edit-body="editBody"></EditFrom>
      </div>
    </div>
  </div>
</template>

<script>
import MemoHeader from './components/MemoHeader.vue'
import ModeTitle from './components/ModeTitle.vue'
import EditFrom from './components/EditFrom.vue'

const STORAGE_KEY = 'memo-spa'
const memoStorage = {
  fetch: function() {
    const memos = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]')

    memos.forEach(function(memo, index) {
      memo.id = index
    })
    memoStorage.uid = memos.length
    return memos
  },
  save: function(memos) {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(memos))
  }
}

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
      editBody: '',
      memos: memoStorage.fetch()
    }
  },
  methods: {
    editable(memo) {
      this.editMode = !this.editMode
      this.editBody = memo.body
    },
    creatable() {
      this.editMode = !this.editMode
      this.editBody = '新規メモ'
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
