<template>
  <div>
    <div id="app">
      <TodoListTitle :title="title"></TodoListTitle>
      <div class="container">
        <FormInput @addTodo="addTodo"></FormInput>
        <TodoList :list="list" @delTodo="delTodo"></TodoList>
        <FooterTotal :list="list" @clear="clear"></FooterTotal>
      </div>
    </div>
    <FooterCopyright></FooterCopyright>
  </div>
</template>

<script>
import TodoListTitle from './components/TodoListTitle.vue'
import FormInput from './components/FormInput.vue'
import TodoList from './components/TodoList.vue'
import FooterTotal from './components/FooterTotal.vue'
import FooterCopyright from './components/FooterCopyright.vue'

export default {
  name: 'App',
  components: {
    FooterCopyright,
    FooterTotal,
    TodoList,
    FormInput,
    TodoListTitle
  },
  data() {
    return {
      title: 'TodoList',
      // 列表数据。在父组件中初始化列表数据，使之子组件全部共用该列表数据
      list: [
        { "id": 1, "text": "吃饭" },
        { "id": 2, "text": "睡觉" },
        { "id": 3, "text": "打豆豆" }
      ]
    }
  },
  methods: {
    addTodo(newTodo) {
      this.list.push({
        "id": this.list.length + 1,
        "text": newTodo
      })
    },
    delTodo(id) {
      this.list = this.list.filter(item => item.id !== id)
    },
    clear() {
      this.list = []
      localStorage.removeItem('list', JSON.stringify(this.list))
    },
    // 数据持久化
    saveList() {
      localStorage.setItem('list', JSON.stringify(this.list))
    }
  },
  created() {
    // 数据持久化
    this.list = JSON.parse(localStorage.getItem('list')) || this.list
  },
  // 数据更新，重新渲染
  updated() {
    this.saveList()
  }
}
</script>

<style scoped>
* {
  margin: 0px;
  padding: 0px;
}

#app {
  width: 550px;
  margin: 0 auto;
}

.container {
  background-color: #eee;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
  box-shadow: 0 0 10px #ccc;
}
</style>
