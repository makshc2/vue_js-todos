<template>
 <div>
   <todo-list v-bind:todos="todos">
   </todo-list>
 </div>
</template>

<script>
import TodoList from './components/TodoList'
import Todo from './components/Todo'

export default {
  name: 'app',
  components: {
    TodoList,
    Todo
  },
  data () {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: true
      },
      {
        title: 'Todo B',
        project: 'Project B',
        done: false
      },
      {
        title: 'Todo C',
        project: 'Project C',
        done: false
      },
      {
        title: 'Todo D',
        project: 'Project D',
        done: false
      }]
    }
  }
}
</script>

<style>

</style>
