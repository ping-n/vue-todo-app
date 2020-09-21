<template>
  <div id="app">
    <h1>{{ title }}</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList ";

export default {
  name: "App",
  components: {
    TodoList
  },
  data() {
    return {
      title: "ToDo App",
    };
  },
};
</script>

<style lang="scss"></style>
