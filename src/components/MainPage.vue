<template>
  <h1>Todo Vue 3</h1>
  <hr />
  <TodoInput @todoSaved="(t) => todoSaved(t)" />
  <TodosContainer :todos="todos" />
</template>
<script>
import TodoInput from "./TodoInput.vue";
import TodosContainer from "./TodosContainer.vue";

export default {
  components: {
    TodoInput,
    TodosContainer,
  },
  name: "MainPage",
  emits: [],
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    todoSaved(todo) {
      const newTodo = { id: this.todos.length++, text: todo, done: false };
      this.todos.push(newTodo);
    },
  },
  mounted() {},
};
</script>

<style scoped>
h1 {
  margin: 40px 0 0;
}
</style>