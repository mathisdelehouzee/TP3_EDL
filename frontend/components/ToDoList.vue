<template>
  <div class="to-do-container">
    <to-do-item-create v-on:create="createItem" />
    <div class="to-do-list-container">
      <to-do-list-item v-for="todo in todos" :key="todo.id" :todo="todo" v-on:delete="deleteItem" />
    </div>
  </div>
</template>

<script>

import ToDoItemCreate from '~/components/ToDoItemCreate.vue'
import ToDoListItem from '~/components/ToDoListItem.vue'

export default {
  components: {
    ToDoItemCreate,
    ToDoListItem
  },
  props: {
    todos: {
      type: Array,
      default () {
        return []
      }
    }
  },
  methods: {
    createItem (item) {
      this.todos.push(item)
    },
    deleteItem (item) {
      this.todos.splice(this.todos.indexOf(item), 1)
    }
  }
}
</script>

<style lang="scss">
.to-do-container {
  width: 400px;
  margin: auto;
  margin-top: 50px;
  display: block;

  .create-container {
    width: 100%;
    height: 50px;
    box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.1);

    input {
      height: 50px;
      width: 250px;
      border: none;
      padding-left: 10px;
      margin-top: 0px;
      font-family: "Quicksand", "Source Sans Pro", -apple-system,
        BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial,
        sans-serif;
      font-size: 18px;
      &:focus {
        outline: none;
      }
    }

    button {
      height: 45px;
      float: right;
      background: none;
      width: auto;
      margin: 0;
      border: none;
      cursor: pointer;
      text-align: right;
      padding-right: 20px;
      font-size: 18px;
      &:focus {
        outline: none;
      }
    }
  }
}
.to-do-list-container {
  width: 400px;
  margin: auto;
  margin-top: 50px;
  display: block;
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.1);
}
</style>
