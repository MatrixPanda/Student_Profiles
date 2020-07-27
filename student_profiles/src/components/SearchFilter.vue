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
        filteredStudent: function() {
            return this.students.filter((student) => {
                return student.firstName.match(this.search);
            });
        }
    }
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