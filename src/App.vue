<template>
  <b-container id="app">
    <h1>{{ title }}</h1>
    <AddTodo v-on:add-todo="addTodo" />
    <TodoList :todos="todos" @delete-todo="deleteTodo" />
  </b-container>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
import moment from "moment";
import shortid from "shortid";

export default {
  name: "App",
  components: {
    TodoList,
    AddTodo,
  },
  data() {
    return {
      title: "Todo App",
      todos: [
        {
          id: shortid.generate(),
          task: "Learn Vue",
          date: moment().format("ll"),
          completed: false,
        },
        {
          id: shortid.generate(),
          task: "Learn Vuex",
          date: moment().format("ll"),
          completed: false,
        },
        {
          id: shortid.generate(),
          task: "Make App",
          date: moment().format("ll"),
          completed: false,
        },
      ],
    };
  },
  methods: {
    addTodo(newTodoObj) {
      this.todos = [...this.todos, newTodoObj];
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter((todo) => todo.id !== todoId);
    },
  },
  mounted() {
    if (localStorage.getItem("todos")) {
      this.todos = JSON.parse(localStorage.getItem("todos"));
    }
  },
  watch: {
    todos: {
      handler() {
        localStorage.setItem("todos", JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
};
</script>

<style lang="scss"></style>
