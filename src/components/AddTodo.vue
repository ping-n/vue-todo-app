<template>
  <div class="add-todo">
    <form @submit.prevent="addTodo">
      <input type="text" name="task" v-model="task" />
      <button type="submit">Add</button>
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
