<template lang="">
    <div class="text-xs-center">
        <v-dialog
            v-model="show"
            width="500"
            persistent
         >       
         <v-card class="padding">
        <v-card-title
          class="headline -2"
          primary-title
          dark
        >
          Add Todo
        <v-spacer></v-spacer>
        <v-btn icon @click="$emit('triggerModal')">
          <v-icon>
            clear
          </v-icon>
        </v-btn>
        </v-card-title>
        <v-card-text>
           <v-text-field
              label="Title"
              v-model='title'
              required
            ></v-text-field>
        </v-card-text>
        <v-card-actions>
          <div class="paragraph font-weight-light"  style="margin-left:10px;" v-show="warning"> Empty title todo cannot be made</div>
          <v-spacer></v-spacer>
        <v-btn flat color="black lighten-2" class="button" dark @click="addTodo">
          <v-icon>create</v-icon>
          Add
        </v-btn>
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
      title: "",
      warning: false
    };
  },
  methods: {
    addTodo(e) {
      if (this.title === "") {
        this.warning = true;
        return;
      }
      this.warning = false;
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
.padding {
  padding: 10px;
}
</style>