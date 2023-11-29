<template>
<h3>Add Task</h3>
<div class="form">
    <input type="text"  v-model="title" >
    <button type="button" v-on:click="addTask">Add</button>
</div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'AddComp',
    data() {
        return {
            title:''
        }
    },
    methods:
    {
        async addTask() {
            let reply = await axios.post("http://localhost:3000/task", {
                title: this.title
            });
            console.warn(reply);
            alert("Task added successfully")
        }
    }
    
}

</script>