<template>
    <div>
        <v-layout row wrap>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
        </div>
        </v-layout>
    </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: "todos",
  props: ["todos"],
  components: {
    TodoItem
  }
};
</script>

<style scoped>
</style>