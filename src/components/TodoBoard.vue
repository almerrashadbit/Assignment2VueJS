<template>
    <div>
      <form @submit.prevent="addNewTodo">
        <input type="text" v-model="newTodoText" placeholder="Enter your todo..." />
        <button type="submit">Add Todo</button>
      </form>
      <TodoItems :todos="todos" @deleteTodo="deleteTodo" @changeStatusTodo="changeStatusTodo" />
    </div>
  </template>
  
  <script>
  import TodoItems from "./TodoItems.vue";
  
  export default {
    name: "TodoBoard",
    components: {
      TodoItems,
    },
    props: ["todos"],
    data() {
      return {
        newTodoText: "",
      };
    },
    methods: {
      addNewTodo() {
        if (this.newTodoText.trim() !== "") {
          const newTodo = {
            id: Date.now(),
            text: this.newTodoText,
            completed: false,
          };
          this.$emit("addTodo", newTodo);
          this.newTodoText = "";
        }
      },
      deleteTodo(todoId) {
        this.$emit("deleteTodo", todoId);
      },
      changeStatusTodo(todoId) {
        this.$emit("changeStatusTodo", todoId);
      },
    },
  };
  </script>

<style>
.todo-board {
  margin-bottom: 10px; /* Add margin bottom */
}
</style>
  