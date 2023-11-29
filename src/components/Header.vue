<template>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="add">Add Task</router-link>
        <router-link to="update">Update Task</router-link>
        <!-- <router-link to="delete">Update Task</router-link> -->
        <a href="#" v-on:click="logout">Logout</a>
    </div>
</template>

<script>
export default {
    name: 'HeaderComp',
    methods: {
        logout() {
            localStorage.clear();
            this.$router.push({name:"Login"});
        }
    }
}
</script>

<style>
.nav{
        background: #222;
    overflow: hidden;
    height: 30px;
    line-height: 30px;
}
.nav a {
    color: white;
    padding: 20px;
    text-decoration: none;
}

.nav a:hover{
    background-color: #2222; 
    color: skyblue;
}

</style>