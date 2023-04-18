<template>
  <div id="app">
    <TodosComponent v-bind:todos="todos"/>
  </div>
  {{ msg }}
</template>

<script>
import TodosComponent from './components/TodosComponent'
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    TodosComponent
  },
  data() {
    return {
      todos: [
        {
          //Array of objects
          id: 1,
          title: 'Todo one',
          completed: false
        },
        {
          //Array of objects
          id: 1,
          title: 'Todo two',
          completed: true
        },
        {
          //Array of objects
          id: 1,
          title: 'Todo three',
          completed: true
        },
      ]
    }
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
</style>

