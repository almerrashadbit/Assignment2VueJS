<template>
    <ol>
      <li v-for="todo in todos" :key="todo.id">
        <input type="checkbox" @change="changeStatus(todo.id)">
        <span :class="{ completed: todo.completed }"><strong class="textTodo">{{ todo.text }}</strong></span>
        <button @click="deleteThis(todo.id)">Delete</button>
        <br>
        <span>Created:</span>
        <span>{{ todo.createdWhen }}</span>
        <br>
        <span>Deadline:</span>
        <span>{{ todo.deadline }}</span>
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

  .textTodo {
    color: aqua;
  }

  span {
    margin-right: 5px;
  }

  button {
    padding: 5px 10px;
    font-size: 12px;
  }
  
  </style>
  