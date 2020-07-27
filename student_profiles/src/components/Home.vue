<template>
  <div >
    <form>
      <input id="name-input" type="text" v-model="searchName" placeholder="Search by name">
    </form>
    <form>
      <input id="tag-input" type="text" v-model="searchTag" placeholder="Search by tags">
    </form>

    <div class="profile-container" v-bind:key="student.id" v-for="student in filteredNames">
      <img v-bind:src='student.pic'>
      <div>
          <h1> {{ student.firstName }} {{ student.lastName }} </h1>
          <div class="details">
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
            <ExpandedInfo id="expand" v-bind:student="student" />
          </div>
      </div>
    </div>

  </div>
</template>

<script>
import ExpandedInfo from './ExpandedInfo.vue';

export default {
  name: 'Home',
  components: {
    ExpandedInfo,
  },
  props: ["students"],
  methods: {
    getAvg(arr) {
        return arr.reduce((a,b) => parseInt(a) + parseInt(b), 0) / arr.length;
    },
  },

  data() {
        return {
            searchName: ''
        }
    },
    computed: {
        filteredNames: function() {
          var self=this;
          return this.students.filter(function(student){
            return student.firstName.toLowerCase().indexOf(self.searchName.toLowerCase())>=0 
                   || student.lastName.toLowerCase().indexOf(self.searchName.toLowerCase())>=0;});
        }
    },

}
</script>


<style scoped>
    #expand {
      display: none;
    }

    img {
        align-self: start;
        border-radius: 100%;
        border: 1px solid var(--primary-color);
        width: 150px;
        height: 150px;
        margin: 2rem;
    }
    
    h1 {
        text-transform: uppercase;
    }
    
    .profile-container {
        display: flex;
        border-bottom: 1px solid var(--primary-color);
        font-size: large;
    }

    .details {
        margin-left: 1.3rem;
    }
</style>

