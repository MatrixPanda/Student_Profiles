<template>
  <div class="profile-container">
    <form>
        <input id="name-input" type="text" v-model="search" placeholder="Search by name">
    </form>
    <div v-bind:key="student.id" v-for="student in students">
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
export default {
  name: "Profile",
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
        filteredStudent: function() {
            return this.students.filter((student) => {
                return student.firstName.match(this.search);
            });
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
