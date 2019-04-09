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
        <span class="text">
        <v-card-text >
          Enter title of Todo to create
        </v-card-text>
        </span>
        <v-card-actions>
        <v-text-field
              label="Title"
              v-model='title'
              required
            ></v-text-field>
        <v-btn flat color="blue lighten-2" class="button" dark @click="addTodo">Create</v-btn>
        </v-card-actions>
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
      if (e === "") return;
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
text {
  float: left;
}
</style>