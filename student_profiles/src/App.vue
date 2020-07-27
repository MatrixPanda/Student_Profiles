<template>
  <div id="app">
    <SearchFilter />
    <Home v-bind:students="students" />
  </div>
</template>

<script>
import axios from 'axios';
import Home from './components/Home.vue';
import SearchFilter from './components/SearchFilter.vue';

export default {
  name: 'App',
  components: {
    Home,
    SearchFilter,
  },
  data() {
    return {
      students: []
    }
  },
  created() {
    axios.get('https://www.hatchways.io/api/assessment/students')
      .then(res => this.students = res.data.students)
      .catch(err => console.log(err));
  },
}
</script>

<style>
:root {
    --primary-color: #D0D0D0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
