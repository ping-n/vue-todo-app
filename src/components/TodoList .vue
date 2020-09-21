<template>
  <div class="todo">
    <h2>Current ToDo list:</h2>
    <div class="todo-list" v-for="todo in todos" :key="todo.id">
      <div class="todo-item">{{ todo.task }} <span class="todo-item-date">{{ todo.date }}</span></div>
      
    </div>
    <AddTodo />
  </div>
</template>

<script>
import AddTodo from "@/components/AddTodo";
import moment from "moment";
import shortid from "shortid";

export default {
  name: "TodoList",
  components: {
    AddTodo,
  },
  data() {
    return {
      todos: [
        {
          id: shortid.generate(),
          task: "Learn Vue",
          date: moment().format("ll"),
        },
        {
          id: shortid.generate(),
          task: "Learn Vuex",
          date: moment().format("ll"),
        },
        {
          id: shortid.generate(),
          task: "Make App",
          date: moment().format("ll"),
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped></style>
