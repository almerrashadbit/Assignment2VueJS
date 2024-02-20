<template>
    <ol>
      <li v-for="todo in todos" :key="todo.id">
        <input type="checkbox" @change="changeStatus(todo.id)">
        <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
        <button @click="deleteThis(todo.id)">Delete</button>
      </li>
    </ol>
  </template>
  
  <script>
  export default {
    name: "TodoItems",
    props: ["todos"],
    methods: {
      deleteThis(todoId) {
        this.$emit("deleteTodo", todoId);
      },
      changeStatus(todoId) {
        this.$emit("changeStatusTodo", todoId);
      },
    },
  };
  </script>
  
  <style scoped>
  .completed {
    text-decoration: line-through;
  }
  
  </style>
  