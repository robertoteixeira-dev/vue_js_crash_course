<template>
    <div>
       <div v-for="todo in todos"
       :key="todo">
        <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
       </div>
    </div>    
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    name: "TodosComponent",
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style scoped>

</style>