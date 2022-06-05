<template>
  <header class="header">
    <h1>{{ title }}</h1>
    <input
      class="new-todo"
      placeholder="What needs to be done?"
      @keyup.enter="create"
      autofocus
    />
  </header>
</template>

<script>
export default {
  name: "TodoInput",
  props: {
    title: { type: String, default: "d todos" },
  },
  methods: {
    create(ev) {
      this.$emit("newTodo", ev.target.value);
      ev.target.value = "";
    },
  },
};
</script>