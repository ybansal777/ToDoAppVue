<script>
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'App',
  components: {
    ToDoList
  }
};
</script>

<template>
    <ToDoList />
</template>

<style>
  body {
    background-image: url(https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTtkNjmeXdvy8_QgArXtDdVVyto15WOae6VSg&s);
    background-color: rgba(255,255,255,0.1);
    background-blend-mode: lighten;
  }
</style>
