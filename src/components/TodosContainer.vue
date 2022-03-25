<template>
  <ul>
    <li>
      <button type="button" @click="() => filterTodos(-1)">
        All [{{ all }}]
      </button>
    </li>
    <li>
      <button type="button" @click="() => filterTodos(1)">
        Done [{{ done }}]
      </button>
    </li>
    <li>
      <button type="button" @click="() => filterTodos(0)">
        Pending [{{ all - done }}]
      </button>
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
  props: ["todos", "all", "done"],
  emits: ["todoDeleted", "todoEdit", "showFiltered"],
  data() {
    return {};
  },
  methods: {
    filterTodos(type) {
      // type => -1: All   1: Done    0: Pending
      this.$emit("showFiltered", type);
    },
  },
  mounted() {},
};
</script>
  
  <style scoped>
h3 {
  margin: 40px 0 0;
}
</style>