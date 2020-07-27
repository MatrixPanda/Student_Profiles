<template>
  <div>
    <div v-bind:key="student.id" v-for="student in students">
      <Profile v-bind:student="student" />
    </div>
  </div>
</template>

<script>
import Profile from './Profile.vue';

export default {
  name: 'Home',
  components: {
    Profile
  },
  props: ["students"],
}
</script>


<style scoped>
/* h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
} */
</style>
