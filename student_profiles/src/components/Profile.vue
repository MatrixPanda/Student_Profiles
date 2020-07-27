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
       <small>Average: {{ student.email }}</small>
       <br>

    </p>
  </div>
</template>

<script>
export default {
  name: "Profile",
  props: ["student"],
}
</script>


<style scoped>

</style>
