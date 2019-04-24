<template>
  <div id="app" class="App">
    <div class="App-Container">
      <img class="Logo" :src="logo" alt="Vue logo"/>
      <h1 class="App-Header">Vue To Do</h1>
      <div>
        <div>
          <input class="input" placeholder="Task" v-model="todo"/>
          <span class="btn btn-success" @click=addItem()> Add </span>
        </div>
        <div>
          <ul class="ToDo-List">
            <ToDoItem v-for="todo in todos"
                      :todo="todo"
                      @delete="OnDeleteItem(todo)"
                      :key="todo.Id"
            />
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

import ToDoItem from './components/ToDoItem.vue'
import Logo from './assets/logo.png';

export default {
  name: 'to-do',
  components: {
    ToDoItem
  },
  data() {
      return {
          logo: Logo,
          todo: '',
          todos: []
      }
  },
  methods: {
    addItem() {
      if (this.todo === '') {
        return
      }

      var newID = this.todos.length
      this.todos = this.todos.concat({Id: newID, Item: this.todo})
    },
    OnDeleteItem(todo) {
      this.todos = this.todos.filter(item => item !== todo)
    }
  }
}
</script>

<style>
  body {
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, Helvetica Neue, Helvetica, Arial, sans-serif;
    height: auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .Logo {
    width: 90px;
    position: relative;
    top: 50px;
  }

  .App {
    text-align: center;
    border: 1px solid white;
    width: 80vw;
    height: auto;
    background: #ffffff;
    padding-bottom: 60px;
    margin: 40px auto;
  }

  .App-Header {
    color: #00bb7e;
    font-weight: 500;
    margin: 70px auto 30px;
    font-size: 2.5em;
  }

  .App-Container {
    width: 80%;
    margin: 0 auto;
  }

  input {
    width: 45%;
    padding: 10px;
    font-size: 1em;
    height: 3em;
    margin: 10px auto;
  }

  .ToDo-List {
    display: inline-flex;
    justify-content: center;
    flex-direction: column-reverse;
    align-items: center;
    list-style: none;
  }
</style>


