<template>
  <b-container>
    <p v-on:click="markComplete">{{ todo.task }}</p>
    <b-button variant="danger" @click="$emit('delete-todo', todo.id)">Delete</b-button>
  </b-container>
</template>

<script>
export default {
  name: "Todo",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style lang="scss" scoped>
.completed {
  text-decoration: line-through;
}
</style>
