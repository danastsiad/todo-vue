<template>
  <ul class="todo-list">
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggleTodo="toggleTodo"
      @removeTodo="removeTodo"
    />
  </ul>
</template>

<script lang="ts">
import { defineComponent, type PropType } from "vue";
import TodoItem from "./TodoItem.vue";
import { Todo } from "@/types/Todo";

export default defineComponent({
  components: {
    TodoItem,
  },
  props: {
    todos: {
      type: Array as PropType<Todo[]>,
    },
  },
  methods: {
    toggleTodo(id: number) {
      this.$emit("toggleTodo", id);
    },
    removeTodo(id: number) {
      this.$emit("removeTodo", id);
    },
  },
  emits: {
    toggleTodo: (id: number) => Number.isInteger(id),
    removeTodo: (id: number) => Number.isInteger(id),
  },
});
</script>

<style></style>
