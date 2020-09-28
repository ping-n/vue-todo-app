<template>
  <b-container class="todo">
    <h2>Current ToDo list:</h2>
    <b-list-group>
      <b-list-group-item :key="todo.id" v-for="todo in todos">
        <Todo
          :todo="todo"
          @delete-todo="$emit('delete-todo', todo.id)"
        />
      </b-list-group-item>
    </b-list-group>
  </b-container>
</template>

<script>
import Todo from "./Todo";

export default {
  name: "TodoList",
  components: {
    Todo,
  },
  data() {
    return {
      newTodoTask: "",
    };
  },
  props: ["todos"],
};
</script>

<style lang="scss" scoped></style>
