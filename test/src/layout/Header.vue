<template lang="">
  <v-toolbar  fixed color="primary">
    <v-toolbar-side-icon><v-icon>list</v-icon></v-toolbar-side-icon>
    <v-toolbar-title class="dark--text">Todo List</v-toolbar-title>

    <v-spacer></v-spacer>    
  </v-toolbar>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
}
.header a {
  color: #fff;
  padding-right: 5px;
  text-decoration: none;
}
</style>