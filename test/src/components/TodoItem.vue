<template>
    <div class="todo-item">
      <v-card color="success">
        <v-card-title>
            <v-icon
                large
                left
            >
         keyboard_arrow_right
      </v-icon>
            <span class="title font-weight-light">
                {{todo.id}}
            </span>
        </v-card-title>
        <v-card-text class="paragraph font-weight-light" v-bind:class="{'is-complete': todo.completed}">
            {{todo.title}}
        </v-card-text>

        <v-card-actions>
            <v-btn flat @click="markComplete">{{ todo.completed?'Uncomplete':'Complete'}}</v-btn>
            <v-btn color="red lighten-2" dark @click="$emit('del-todo', todo.id)">Delete</v-btn>
        </v-card-actions>
    </v-card>
    </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
    deleteTodo() {}
  }
};
</script>

<style scoped>
.todo-item {
  margin-top: 10px;
  padding: 10px;
}
.is-complete {
  text-decoration: line-through;
}
.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>