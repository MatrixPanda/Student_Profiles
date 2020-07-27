<template>
  <div id="app">
    <Home v-bind:students="students" />
  </div>
</template>

<script>
import axios from 'axios';
import Home from './components/Home.vue';

export default {
  name: 'App',
  components: {
    Home,
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

form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 10px;
  border: none;
  border-bottom: 1px solid var(--primary-color);
  font-size: large;
  outline: none;
}
input[type="text"]:focus {
  border: none;
  border-bottom: 1px solid black;
}
</style>
