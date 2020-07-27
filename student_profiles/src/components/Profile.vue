<template>
  <div class="profile-container">
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
</template>

<script>
export default {
  name: "Profile",
  props: ["student"],
  methods: {
    getAvg(arr) {
        return arr.reduce((a,b) => parseInt(a) + parseInt(b), 0) / arr.length;
    },
  }
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
        /* position: relative; */
        /* display: flex;
        cursor: pointer;
        z-index: 1;
        background-color: #f5f5f5;
        font-family: 'Roboto', sans-serif;
        font-size: 1.3vw;
        font-weight: bold;
        border: none;
        border-radius: 10rem;
        width: 12em;
        height: 4em;
        text-align: left;
        text-decoration: none;
        margin-top: auto;
        margin-bottom: auto;   
        -webkit-transition-duration: 0.4s; 
        transition-duration: 0.4s; 
        box-shadow: -0.8rem 0.9rem 20px rgba(66, 66, 66, 0.3); */
    }
</style>
