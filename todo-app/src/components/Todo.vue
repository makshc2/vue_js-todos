<template>
  <div class="ui centered card">
    <div class="content" v-bind:class="{ 'is-done': todo.done, 'in-progress': !todo.done }" v-show="!isEditing">
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
            <span class="right floated edit icon" v-on:click="showForm">
              <i class="edit icon"></i>
            </span>
            <span class='right floated trash icon' v-on:click="deleteTodo(todo)">
              <i class='trash icon'></i>
            </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="todo.title" >
        </div> <div class='field'>
        <label>Project</label>
        <input type='text' v-model="todo.project" >
      </div>
      <div class='ui two button attached buttons'>
        <button class='ui basic green button' v-on:click="hideForm">Save</button>
        <button class='ui basic green button' v-on:click="hideForm">Cancel</button>
      </div>
      </div>
    </div>
    <div class="ui bottom attached green basic button" v-show="todo.done" @click="todo.done = false">
      Completed
    </div>
    <div class="ui bottom attached red basic button" v-show="!todo.done" @click="todo.done = true">
      Complete
    </div>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  data () {
    return {
      isEditing: false
    }
  },
  methods: {
    deleteTodo (todo) {
      this.$emit('delete-todo', todo)
    },
    showForm () {
      this.isEditing = true
    },
    hideForm () {
      this.isEditing = false
    }
  }
}
</script>

<style scoped>
  .edit:hover{
    cursor: pointer;
    color: red;
  }
  .is-done{
    background-color: green !important;
  }
  .in-progress{
    background-color: yellow !important;
  }
</style>
