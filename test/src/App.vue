<template>
  <div id="app">
    <Header v-on:triggerModal='triggerModal'/>
    <AddTodo v-bind:show='showModal' v-on:add-todo="addTodo" v-on:triggerModal='triggerModal'/>
    <Todos v-bind:todos='todos' v-on:del-todo="delTodo"/>
    <BottomNav v-on:triggerModal='triggerModal'/>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import Header from "./layout/Header.vue";
import AddTodo from "./components/AddTodo.vue";
import BottomNav from "./components/BottomNav.vue";
export default {
  name: "app",
  components: {
    Todos,
    Header,
    AddTodo,
    BottomNav
  },
  methods: {
    delTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(todo) {
      fetch("https://jsonplaceholder.typicode.com/todos", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify({
          completed: todo.completed,
          title: todo.title
        })
      })
        .then(res => res.json())
        .then(json => {
          this.showModal = !this.showModal;
          this.todos = [...this.todos, json];
        });
    },
    triggerModal() {
      this.showModal = !this.showModal;
    }
  },
  data() {
    return {
      todos: [],
      showModal: false
    };
  },
  created() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=25", {
      method: "GET"
    })
      .then(res => res.json())
      .then(json => (this.todos = json));
  }
};
</script>

<style>
body {
  line-height: 1.4;
  font-family: Arial, Helvetica, sans-serif;
}
</style>
