<template>
  <b-container class="add-todo">
    <b-form @submit.prevent="addTodo">
      <b-form-input type="text" name="task" v-model="task" />
      <b-button type="submit">Add</b-button>
      <b-alert v-if="alert" show variant="danger"> {{this.alert}} </b-alert>
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
      alert: "",
    };
  },
  methods: {
    addTodo() {
      if (this.task.length > 0) {
        const newTodoObj = {
          id: shortid.generate(),
          task: this.task,
          date: moment().format("ll"),
          completed: false,
        };
        this.$emit("add-todo", newTodoObj);
        this.alert = "";
        this.task = "";
      } else {
        this.alert = "Please input a task"
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
