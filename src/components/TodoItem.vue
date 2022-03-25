<template>
  <div class="row">
    <input type="checkbox" v-model="currentTodo.done" />
    <label :class="{ done: currentTodo.done }"
      >{{ currentTodo.id }} - {{ currentTodo.text }}</label
    >
    <button @click="editTodo">Edit</button>
    <button @click="deleteTodo">Delete</button>
  </div>
</template>
  <script>
export default {
  components: {},
  name: "TodoItem",
  props: ["todo"],
  emits: ["todoDeleted", "todoEdit"],
  data() {
    return {
      n: this.todo.id,
    };
  },
  methods: {
    deleteTodo() {
      this.$emit("todoDeleted", this.currentTodo.id);
    },
    editTodo() {
      this.$emit("todoEdit", this.currentTodo.id);
    },
  },
  mounted() {},
  computed: {
    currentTodo() {
      return this.todo;
    },
  },
};
</script>
  
  <style scoped>
.row {
  margin: 10px 0 0;
}
.done {
  text-decoration: line-through;
}
</style>