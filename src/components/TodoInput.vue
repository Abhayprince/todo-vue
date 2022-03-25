<template>
  <p v-if="todo.id">You are modifying: [{{ existing }}]</p>
  <input type="text" v-model="todo.text" placeholder="Add a new todo" />
  <button type="button" @click="add">{{ todo.id > 0 ? "Save" : "Add" }}</button>
</template>
  <script>
export default {
  components: {},
  name: "TodoInput",
  props: {
    todotoedit: Object,
  },
  emits: ["todoSaved"],
  data() {
    return {
      todo: { id: 0, text: "", done: false },
      existing: "",
    };
  },
  methods: {
    add() {
      this.$emit("todoSaved", this.todo);
      this.todo = { id: 0, text: "", done: false };
      this.existing = null;
    },
  },
  mounted() {
    if (this.todotoedit) this.todo = this.todotoedit;
  },
  watch: {
    todotoedit(newVal, oldVal) {
      console.log("Old value was: " + JSON.stringify(oldVal));
      this.todo = { ...newVal };
      this.existing = newVal?.text;
    },
  },
};
</script>
  
  <style scoped>
h3 {
  margin: 40px 0 0;
}
</style>