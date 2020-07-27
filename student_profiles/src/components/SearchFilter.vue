<template>
    <div>
        <form>
            <input id="name-input" type="text" name="title" placeholder="Search by name">
        </form>
    </div>
</template>

<script>
export default {
    name: "SearchFilter"

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