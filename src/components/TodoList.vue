<template>
  <div class="todo-list">
    <TodoItem
      v-for="todo of todos"
      :key="todo.id"
      :todo="todo"
      @todoDeleted="(id) => $emit('todoDeleted', id)"
      @todoEdit="(id) => $emit('todoEdit', id)"
    />
  </div>
</template>
  <script>
import TodoItem from "./TodoItem.vue";

export default {
  components: { TodoItem },
  name: "TodoList",
  props: ["todos"],
  emits: ["todoDeleted", "todoEdit"],
  data() {
    return {};
  },
  methods: {},
  mounted() {},
};
</script>
  
  <style scoped>
h3 {
  margin: 40px 0 0;
}
</style>