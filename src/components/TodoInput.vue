<template>
  <input type="text" v-model="todo" placeholder="Add a new todo" />
  <button type="button" @click="add">Add</button>
</template>
  <script>
export default {
  components: {},
  name: "TodoInput",
  props: {
    todotoedit: String,
  },
  emits: ["todoSaved"],
  data() {
    return {
      todo: "",
    };
  },
  methods: {
    add() {
      this.$emit("todoSaved", this.todo);
    },
  },
  mounted() {
    if (this.todotoedit) this.todo = this.todotoedit;
  },
};
</script>
  
  <style scoped>
h3 {
  margin: 40px 0 0;
}
</style>