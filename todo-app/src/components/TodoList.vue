<template>
    <div class="todolist">
      <p>Compleded Task: {{todos.filter(todo => {return todo.done === true}).length}}</p>
      <p>Pending Task: {{todos.filter(todo => {return todo.done === false}).length}}</p>
      <div class="ui centered card" v-for="todo in todos" :key="todo.id">
        <div class="content" v-bind:class="{ 'is-done': todo.done, 'in-progress': !todo.done }">
          <div class="header">
            {{todo.title}}
          </div>
          <div class="meta">
            {{todo.project}}
          </div>
          <div class="meta">
            {{todo.done === true ? 'Done' : 'In progress'}}
          </div>
          <div class="extra content">
            <span class="right floated edit icon">
              <i class="edit icon"></i>
            </span>
          </div>
        </div>
        <div class="ui bottom attached green basic button" v-show="todo.done" @click="todo.done = false">
          Completed
        </div>
        <div class="ui bottom attached red basic button" v-show="!todo.done" @click="todo.done = true">
          Complete
        </div>
      </div>
    </div>
</template>

<script type = "text/javascript">
export default {
  props: ['todos']
}
</script>

<style scoped>
  .todolist {
    display: flex;
    flex-direction: column;
    width: 1200px;
    margin:50px auto;
  }
  .is-done{
    background-color: green !important;
  }
  .in-progress{
    background-color: yellow !important;
  }
</style>
