<template>
  <footer class="footer">
    <!-- This should be `0 items left` by default -->
    <span class="todo-count">
      <strong>{{ active_todos }}</strong> item left
    </span>
    <!-- Remove this if you don't implement routing -->
    <ul class="filters">
      <li>
        <a
          @click.prevent="createFilter('all')"
          :class="{ selected: calculateSelected('all') }"
          href
          >All</a
        >
      </li>
      <li>
        <a
          @click="createFilter('active')"
          :class="{ selected: calculateSelected('active') }"
          >Active</a
        >
      </li>
      <li>
        <a
          @click="createFilter('completed')"
          :class="{ selected: calculateSelected('completed') }"
          >Completed</a
        >
      </li>
    </ul>
    <!-- Hidden if no completed items are left ↓ -->
    <button @click="clicked" class="clear-completed">Clear completed</button>
  </footer>
</template>

<script>
export default {
  name: "TodosActions",
  props: {
    items: { type: Array },
    filter: { type: String },
  },
  computed: {
    active_todos: function () {
      return this.items.filter((x) => x.isCompleted == false).length;
    },
  },
  methods: {
    calculateSelected: function (cls) {
      return this.filter == cls;
    },
    createFilter(filter) {
      // this.filter = filter;
      this.$emit("filterEvent", filter);
    },
    clicked() {
      this.$parent.clearCompleted();
    },
  },
};
</script>

