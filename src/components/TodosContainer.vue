<template>
  <ul>
    <li>
      <button type="button">All [{{ all }}]</button>
    </li>
    <li>
      <button type="button">Done [{{ done }}]</button>
    </li>
    <li>
      <button type="button">Pending [{{ pending }}]</button>
    </li>
  </ul>
  <TodoList
    :todos="todos"
    @todoDeleted="(id) => $emit('todoDeleted', id)"
    @todoEdit="(id) => $emit('todoEdit', id)"
  />
</template>
  <script>
import TodoList from "./TodoList.vue";

export default {
  components: {
    TodoList,
  },
  name: "TodosContainer",
  props: ["todos"],
  emits: ["todoDeleted", "todoEdit"],
  data() {
    return {};
  },
  methods: {},
  mounted() {},
  computed: {
    all() {
      return this.todos.length;
    },
    done() {
      return this.todos.filter((t) => t.done).length;
    },
    pending() {
      return this.todos.filter((t) => !t.done).length;
    },
  },
};
</script>
  
  <style scoped>
h3 {
  margin: 40px 0 0;
}
</style>