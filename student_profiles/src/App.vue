<template>
  <div id="app">
    <Home v-bind:students="students" />
  </div>
</template>

<script>
import Home from './components/Home.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Home
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
  /* text-align: center; */
  /* color: #2c3e50; */
  /* margin-top: 60px; */
}
</style>
