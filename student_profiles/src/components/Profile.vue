<template>
  <div>
    <img v-bind:src='student.pic'>
    <p>
       <strong>{{ student.firstName }} {{ student.lastName }}</strong>
       <br>
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

</style>
