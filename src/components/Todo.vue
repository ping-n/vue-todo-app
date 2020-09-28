<template>
  <div>
    <div v-bind:class="{ completed: todo.completed }">
      <p v-on:click="markComplete">{{ todo.task }}</p>
      <button @click="$emit('delete-todo', todo.id)">Delete</button>
    </div>
  </div>
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
