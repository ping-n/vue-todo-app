<template>
  <div class="add-todo">
    <form @submit.prevent="addTodo">
      <input type="text" name="task" v-model="todo.task" />
    </form>
  </div>
</template>

<script>
import moment from "moment";
import shortid from "shortid";

export default {
  name: "AddTodo",
  data() {
    return {
      todo: {
        id: null,
        task: "",
        date: null,
      },
    };
  },
  methods: {
    addTodo() {
      return {
        id: this.todo.id = shortid.generate(),
        task: this.todo.task,
        date: this .todo.date = moment().format("ll")
      }
    }
  },
};
</script>

<style lang="scss" scoped></style>
