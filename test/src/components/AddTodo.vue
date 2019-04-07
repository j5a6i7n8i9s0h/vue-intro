<template lang="">
    <div class="text-xs-center">
        <v-dialog
            v-model="show"
            width="500"
         >       
         <v-card>
        <v-card-title
          class="headline -2"
          primary-title
          dark
        >
          Add Todo
        </v-card-title>

        <v-card-text>
        <input type="text" name="title" v-model="title" placeholder="Add Todo.."/>
        
        </v-card-text>
        <v-card-action>
        <v-btn color="blue lighten-2" dark @click="addTodo">Create</v-btn>
        </v-card-action>
        </v-card>
        </v-dialog>
    </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        title: this.title,
        completed: false
      };
      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  },
  props: ["show"]
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>