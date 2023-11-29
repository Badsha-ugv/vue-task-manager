<template>
    <h3>Update Task</h3>
    <div class="form">
        <input type="text"  v-model="tasks.title">
        <button type="button" v-on:click="updateTask">Update</button>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: 'UpdateComp',
    data() {
        return {
            tasks: {
                id:'',
                title:'',
            }
        }
    },
    methods: {
        async updateTask() {
            let reply = await axios.put("http://localhost:3000/task/"+this.$route.params.id, {
                title: this.tasks.title,
              
            });
            console.warn(reply);
            alert("Task updated successfully")
            this.$router.push({name:'Home'})
        }
    },
    async mounted() {
        console.log('route id', this.$route.params.id);
        let get_task = await axios.get("http://localhost:3000/task/" + this.$route.params.id);
        console.log('get task', get_task.data);
        this.tasks = get_task.data
    }

}

</script>