<template>
  <b-container class="add-todo">
      <b-form @submit.prevent="addTodo">
        <b-form-input type="text" name="task" v-model="task" />
        <b-button type="submit">Add</b-button>
      </b-form>
  </b-container>
</template>

<script>
import moment from "moment";
import shortid from "shortid";

export default {
  name: "AddTodo",
  data() {
    return {
      task: "",
    };
  },
  methods: {
    addTodo() {
      const newTodoObj = {
        id: shortid.generate(),
        task: this.task,
        date: moment().format("ll"),
        completed: false,
      };
      this.$emit("add-todo", newTodoObj);
      this.task = "";
    },
  },
};
</script>

<style lang="scss" scoped></style>
