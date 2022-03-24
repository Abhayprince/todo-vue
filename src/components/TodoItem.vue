<template>
  <input type="checkbox" />
  <label :class="{ done: todo.done }">{{ n }} - {{ todo.text }}</label>
  <button>Delete</button>
</template>
  <script>
export default {
  components: {},
  name: "TodoItem",
  props: ["todo"],
  emits: [],
  data() {
    return {
      n: this.todo.id,
    };
  },
  methods: {},
  mounted() {},
};
</script>
  
  <style scoped>
h3 {
  margin: 40px 0 0;
}
.done {
  text-decoration: line-through;
}
</style>