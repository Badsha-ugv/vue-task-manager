<template>

    <h3>Welcome Home, Hello {{userName}} </h3>

    <table class="task-table">
        <tr>
            <th>Title</th>
            <th>Action</th>
        </tr>
        <tr v-for="task in tasks.data" :key="task">
            <td>{{ task.title }}</td>
            <td><router-link :to="'/update/'+task.id">Update</router-link></td>
            <td><button type="button" v-on:click="deleteTask(task.id)">Delete</button></td>

        </tr>
    </table>

</template>

<script>
import axios from 'axios';



export default {
    name: 'HomeComp',
    data() {
        return {
            userName: '',
            tasks: {
                title:''
            }
        };
    },
    methods: {
        async loadTask() {
            let user = localStorage.getItem('user');

            if (!user) {
                this.$router.push({ name: "Signup" });
            } else {
                this.userName = JSON.parse(user).name;
            }
            let task = await axios.get("http://localhost:3000/task");
            console.warn(task,'get task ');
            this.tasks = task
            console.warn('this task', this.tasks)
        },
        async deleteTask(taskId) {
            let reply = await axios.delete("http://localhost:3000/task/" +taskId);
            if (reply.status == 200) {
                // alert("task deleted successfully")
                this.loadTask()
                console.log("deleted successfully");
            }
        }

    },
    mounted() {
        
        this.loadTask();
    },
    
}
</script>

<style>
.task-table{
        width: 350px;
    border: 1px solid;
    margin: auto;
    padding: 10px;
}
.task-table td {
    border: 1px solid;
    padding: 10px 20px;
    background: #fafafa;
}

</style>