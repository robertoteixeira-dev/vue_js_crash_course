<template>
  <div id="app">
    <HeaderComponent />
    <AddTodo v-on:add-todo="addTodo" />
    <TodosComponent v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
  {{ msg }}
</template>

<script>
import HeaderComponent from './components/layout/HeaderComponent';
import TodosComponent from './components/TodosComponent';
import AddTodo from './components/AddTodo.vue';
import axios from 'axios';
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    TodosComponent,
    AddTodo
  },
  data() {
    return {
      todos: [
        /*{
          //Array of objects
          id: 1,
          title: 'Todo one',
          completed: false
        },
        {
          //Array of objects
          id: 2,
          title: 'Todo two',
          completed: false
        },
        {
          //Array of objects
          id: 3,
          title: 'Todo three',
          completed: false
        },*/
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        // eslint-disable-next-line no-unused-vars
        .then(res => this.todos = 
          this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
      this.todos = [...this.todos, newTodo];
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
}
</script>


<style>

* { 
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>

