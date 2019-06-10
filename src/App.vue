<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h3>Todo List</h3>
    <input v-model="inputValue">
    <button @click="addTodo">Add</button>
    <p>{{warning}}</p>
    <TodoItem v-for="(todo, index) in todos" :key="index" :todo="todo" :index="index" v-on:doneTodo="doneTodo($event)"></TodoItem>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    TodoItem
  },
  data () {
    return {
      inputValue: '',
      todos: [],
      warning: ''
    }
  },
  methods: {
    addTodo(){
      // console.log('add todo', this.inputValue)
      this.todos.push(this.inputValue)
      this.inputValue = ''
      console.log('isi todos: ', this.todos)
    },
    doneTodo(index) {
      this.todos.splice(index, 1)
    }
  },
  watch: {
    inputValue: function (newValue, oldValue) {
      if (this.inputValue.length > 10) {
        // maka akan ada warning
        this.warning = 'Maksimal 10 karakter!'
      } else {
        this.warning = ''
      }
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
  margin-top: 60px;
}
</style>
