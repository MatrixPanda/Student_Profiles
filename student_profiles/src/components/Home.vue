<template>
  <div >
    <input id="name-input" type="text" v-model="search" placeholder="Search by name">

    <div class="profile-container" v-bind:key="student.id" v-for="student in filteredNames">
      <!-- <Profile v-bind:student="student" /> -->
      <img v-bind:src='student.pic'>
      <div>
          <h1> {{ student.firstName }} {{ student.lastName }} </h1>
          <p>
              <small>Email: {{ student.email }}</small>
              <br>
              <small>Company: {{ student.company }}</small>
              <br>
              <small>Skill: {{ student.skill }}</small>
              <br>
              <small>Average: {{ getAvg(student.grades) }}%</small>
              <br>
          </p>
      </div>
    </div>
  </div>
</template>

<script>
// import Profile from './Profile.vue';

export default {
  name: 'Home',
  props: ["students"],
  methods: {
    getAvg(arr) {
        return arr.reduce((a,b) => parseInt(a) + parseInt(b), 0) / arr.length;
    },
  },

  data() {
        return {
            search: ''
        }
    },
    computed: {
        filteredNames: function() {
          var self=this;
          return this.students.filter(function(student){
            return student.firstName.toLowerCase().indexOf(self.search.toLowerCase())>=0 
                   || student.lastName.toLowerCase().indexOf(self.search.toLowerCase())>=0;});
        }
    },

}
</script>


<style scoped>
    img {
        align-self: center;
        border-radius: 100%;
        border: 1px solid var(--primary-color);
        width: 150px;
        height: 150px;
        margin: 2rem;
    }

    p {
        margin-left: 1.3rem;
    }
    
    h1 {
        text-transform: uppercase;
    }
    
    .profile-container {
        display: flex;
        border-bottom: 1px solid var(--primary-color);
        font-size: large;
    }
</style>

