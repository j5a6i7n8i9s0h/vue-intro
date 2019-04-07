<template>
  <div id="app">
    <Header v-on:triggerModal='triggerModal'/>
    <AddTodo v-bind:show='showModal' v-on:add-todo="addTodo"/>
    <Todos v-bind:todos='todos' v-on:del-todo="delTodo"/>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import Header from "./layout/Header.vue";
import AddTodo from "./components/AddTodo.vue";
export default {
  name: "app",
  components: {
    Todos,
    Header,
    AddTodo
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
      console.log("ss");
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
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=5", {
      method: "GET"
    })
      .then(res => res.json())
      .then(json => (this.todos = json));
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  line-height: 1.4;
  font-family: Arial, Helvetica, sans-serif;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
