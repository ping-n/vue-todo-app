<template>
  <div class="todo" :class="{ completed: todo.completed }">
    <p v-show="!isEditing">
      {{ todo.task }}
    </p>
    <div v-show="isEditing">
      <b-form @submit.prevent="hideForm">
        <b-form-input type="text" name="task" v-model="todo.task" />
      </b-form>
    </div>
    <div class="todo-icon">
      <p>{{ todo.date }}</p>
      <b-icon
        class="border rounded p-2"
        font-scale="2"
        icon="hand-thumbs-up"
        @click="markComplete"
      ></b-icon>
      <b-icon
        class="border rounded p-2"
        font-scale="2"
        icon="pencil-square"
        @click="showForm"
      ></b-icon>
      <b-icon
        class="border rounded p-2"
        font-scale="2"
        icon="trash"
        @click="$emit('delete-todo', todo.id)"
      ></b-icon>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: ["todo"],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
    editTodo() {
      console.log("hello");
    },
  },
};
</script>

<style lang="scss" scoped>
.todo {
  display: flex;
  align-content: center;
  justify-content: space-between;
}
.completed {
  background-color: greenyellow;
}
</style>
