<template>
  <h1>Todo Vue 3</h1>
  <hr />
  <TodoInput @todoSaved="(t) => todoSaved(t)" :todotoedit="todoToEdit" />
  <TodosContainer
    :todos="todos"
    @todoDeleted="(id) => deleteTodo(id)"
    @todoEdit="(id) => todoEdit(id)"
  />
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
      todoToEdit: null,
    };
  },
  methods: {
    todoSaved(todo) {
      if (todo.id) {
        //Edit
        const idx = this.todos.findIndex((t) => t.id === todo.id);
        if (idx > -1) {
          this.todos[idx] = { ...todo };
        }
      } else {
        //Add new
        const newTodo = { ...todo, id: this.todos.length + 1 };
        this.todos.push(newTodo);
      }
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    todoEdit(id) {
      this.todoToEdit = this.todos.find((t) => t.id === id);
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