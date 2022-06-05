<template>
  <ul class="todo-list">
    <!-- These are here just to show the structure of the list items -->
    <!-- List items should get the class `editing` when editing and `completed` when marked as completed -->
    <li
      v-for="todo in todos"
      v-bind:key="todo.id"
      :class="{ completed: todo.isCompleted }"
    >
      <div class="view">
        <input
          class="toggle"
          type="checkbox"
          v-bind:checked="!!todo.isCompleted"
          @click="changeTodo(todo)"
        />
        <label>{{ todo.title }}</label>
        <button class="destroy" @click="deleteTodo(todo)"></button>
      </div>
      <input class="edit" value="Rule the web" />
    </li>
  </ul>
</template>

<script>
export default {
  name: "TodosList",
  props: {
    todos: { type: Array },
  },
  methods: {
    changeTodo(ev) {
      ev.isCompleted = !ev.isCompleted;
      this.$parent.saveTodos();
    },
    deleteTodo(todo) {
      this.$parent.deleteTodo(todo);
    },
  },
};
</script>
