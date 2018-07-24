<template>
    <div class="todolist">
      <p>Compleded Task: {{todos.filter(todo => {return todo.done === true}).length}}</p>
      <p>Pending Task: {{todos.filter(todo => {return todo.done === false}).length}}</p>
      <todo v-on:remove-todo="deleteTodo" v-for="todo in todos" :key="todo.id" :todo.sync="todo"></todo>
    </div>
</template>

<script type = "text/javascript">
import Todo from './Todo'
export default {
  components: {
    Todo
  },
  props: ['todos'],
  methods: {
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      console.log(todoIndex)
      this.todos.splice(todoIndex, 1)
    }
  }
}

</script>

<style scoped>
  .todolist {
    display: flex;
    flex-direction: column;
    width: 1200px;
    margin:50px auto;
  }
</style>
