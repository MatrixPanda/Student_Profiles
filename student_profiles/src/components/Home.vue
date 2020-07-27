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
          <button class="expand-btn" @click="setId(student.id)">+</button>
          <!-- <button class="expand-btn" @click="pickedId = student.id">+</button> -->
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

            <!-- <ExpandedInfo id="expand" v-if="$data.selectedId.get(student.id) === true" v-bind:student="student" /> -->
            
            <ExpandedInfo id="expand" v-if="pickedId === student.id" v-bind:student="student" />
            
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
  data() {
    return {
        searchName: '',
        selectedId: new Map(),
        pickedId: '',
    }
  },

  computed: {
    // Note: First name + SPACE + last name doesn't work
    filteredNames: function() {
      var self=this;
      return this.students.filter(function(student){
        return student.firstName.toLowerCase().indexOf(self.searchName.toLowerCase())>=0 
                || student.lastName.toLowerCase().indexOf(self.searchName.toLowerCase())>=0;});
    }
  },

  methods: {
    getAvg(arr) {
        return arr.reduce((a,b) => parseInt(a) + parseInt(b), 0) / arr.length;
    },

    setId(id) {
      this.$data.selectedId.set(id, true, true); // Saves ID, expand for that id is set to true
      console.log("SET: ", this.$data.selectedId.get(id));
      
      if (this.pickedId === id) {
        this.pickedId = '';
      } else {
        this.pickedId = id;
      }

      // console.log("SET: ", this.$data.selectedId.get(id));
      // console.log(this.$data.selectedId);
      // this.expandCheck(id);
      // return this.$data.selectedId.a = true;
    },

    expandCheck(id) {
      console.log(id);
      
      // if (this.$data.selectedId.get(id) === true) {
      //   console.log("show TRUE");
      //   return true;
      // } else {
      //   console.log("show FALSE");
      //   console.log(this.$data.selectedId.get(id));
      //   return false;
      // }
    },
  },

}
</script>


<style scoped>
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
    
    .expand-btn {
      position: absolute;
      border: none;
      background-color: transparent;
      font-size: 4rem;
      font-weight: bold;
      height: 2.5rem;
      width: 2.5rem;
      border-radius: 100%; 
      right: 0%;
      margin-right: 1.5rem;
      margin-top: 1rem;
      color: var(--primary-color);
      cursor: pointer;
    } 
</style>

