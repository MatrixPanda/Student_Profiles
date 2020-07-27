<template>
    <div>
        <form>
            <input id="name-input" type="text" v-model="search" placeholder="Search by name">
        </form>
    </div>
</template>

<script>
export default {
    name: "SearchFilter",
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