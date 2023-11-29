<template>

<h3>Login Page</h3>
    <div class="form">

        
        <input type="email" id="email" name="email" v-model="email" placeholder="Enter email" >
        <input type="password" id="password" name="password" v-model="password" placeholder="Enter password" > <br>
        <button v-on:click="login">Login</button>

        <router-link to="signup" > Register</router-link>
    </div>

</template>

<script>
// import area

import axios from "axios";


export default {
    name: "LoginComp",
    data() {
        return {
            email: '',
            password:'',
        }
    },
    methods: {
        async login() {
            console.log('loign clicked');
            console.log(this.email, this.password);

            let reply = await axios.get(`http://localhost:3000/user?email=${this.email}&password=${this.password}`);

         
            if (reply.status == 200 & reply.data.length > 0) {
                localStorage.setItem("user", JSON.stringify(reply.data));
                this.$router.push({ name: 'Home' });
            }
        }

        
    },
    mounted() {
        let user = localStorage.getItem("user");
        if (user) {
            this.$router.push({ name: 'Home' });
        }
    }
}

</script>