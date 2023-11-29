<template>

<h3>Signup Page</h3>

<div class="form">

    <input type="text" id="name" v-model="name" name="name" placeholder="Enter name" >
    <input type="email" id="email" name="email" v-model="email" placeholder="Enter email" >
    <input type="password" id="password" name="password" v-model="password" placeholder="Enter password" > <br>
    <button v-on:click="signup">Signup</button>

    <router-link to="login">Login</router-link>
</div>

</template>

<script>

// import section
import axios from 'axios'

// end of import section

export default {
    name: 'SignupComp',

    data() {
        return {
            name: '',
            email: '',
            password: '',
        }
    },
    mounted() {
        let user = localStorage.getItem('user');
        if (user) {
            this.$router.push({ name: "Home" });
        }
    },
    methods: {
        async signup() {
            console.log("Signup");
            console.log(this.name, this, this.email, this.password);
            let reply = await axios.post("http://localhost:3000/user/", {
                name: this.name,
                email: this.email,
                password: this.password
            });

            localStorage.setItem("user", JSON.stringify(reply.data));
            if (reply.status == 201) {
                // alert("Success!!")
                this.$router.push({name:"Home"})
            }


        }
    }
}
</script>

<style>

</style>