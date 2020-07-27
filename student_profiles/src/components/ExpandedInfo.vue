<template>
  <div > 
    <div v-bind:key="grade.id" v-for="(grade, i) in student.grades">
        <small style="margin-right: 25px">Test: {{i+1}}</small>
        <small>{{ grade }}%</small>
    </div>

  </div>
</template>

<script>

export default {
  name: 'ExpandedInfo',
  props: ["student"],
}
</script>


<style scoped>

</style>