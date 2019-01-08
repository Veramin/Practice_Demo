<template>
  <div id="app">
      <router-view></router-view>
      <div class="toDoList-Box">
        <Header
          :addToDo="addToDo"
        />
        <List
          :todos = "todos"
          :delToDo = "delToDo"
        />
        <Footer
          :todos = "todos"
          :selectedAll = "selectedAll"
          :delFinishedToDo = "delFinishedToDo"
        />
      </div>
      
  </div>
</template>

<script>
import Header from "./components/Header/Header"
import List from "./components/List/List"
import Footer from "./components/Footer/Footer"

export default {
  name: 'App',
  data() {
    return {
      todos: [
        {title: "8:00起床", finished: true},
        {title: "8:30吃饭", finished: false},
        {title: "9:00吃药", finished: false},
        {title: "9:30开电脑", finished: true},
        {title: "9:31撸代码", finished: true}

      ]
    }
  },
  components: {
    Header,
    List,
    Footer
  },
  methods: {
    // 删除一条记录
    delToDo(index) {
      this.todos.splice(index, 1);
    },
    // 增加一条记录
    addToDo(todo) {
      this.todos.unshift(todo);
    },
    // 选中所有计划
    selectedAll(isCheck) {
      this.todos.forEach(todo => {
        todo.finished = isCheck;
      })
    },
    // 删除所有记录
    delFinishedToDo() {
      this.todos = this.todos.filter(todo => !todo.finished)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 15px;
  width: 1200px;
  height: 100%;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-content: center;
  flex-direction: column;
  
  background-color: lightblue;
}
.toDoList-Box {
  width: 900px;
  height: 100%;
  background-color: #fff;
  margin: 10px auto;
}
</style>
