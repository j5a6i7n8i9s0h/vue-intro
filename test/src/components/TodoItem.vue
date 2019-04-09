<template>
    <div class="todo-item">
      <v-card
        width="400"
      >
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
                        <v-spacer></v-spacer>
                <v-btn icon color="grey lighten" dark @click="$emit('del-todo', todo.id)" flat >
                  <v-icon>clear</v-icon>
                </v-btn>

        </v-card-title>
        <v-card-text class="paragraph font-weight-light" v-bind:class="{'is-complete': todo.completed}">
            {{todo.title}}
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
            <v-btn icon flat @click="markComplete">
               <v-icon >{{ todo.completed?'check_box':'check_box_outline_blank'}}</v-icon>
               </v-btn>
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