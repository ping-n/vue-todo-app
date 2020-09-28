<template>
  <div class="todo">
    <h2>Current ToDo list:</h2>
    <ul>
      <li :key="todo.id" v-for="todo in todos" >
        <Todo :todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)"/>
      </li>
    </ul>
  </div>
</template>

<script>
import Todo from "./Todo";

export default {
  name: "TodoList",
  components: {
    Todo,
  },
  props: ["todos"],
};
</script>

<style lang="scss" scoped></style>
