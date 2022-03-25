<template>
  <h1>Todo Vue 3</h1>
  <hr />
  <TodoInput @todoSaved="(t) => todoSaved(t)" />
  <TodosContainer :todos="todos" @todoDeleted="(id) => deleteTodo(id)" />
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
      const newTodo = { id: this.todos.length + 1, text: todo, done: false };
      this.todos.push(newTodo);
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
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