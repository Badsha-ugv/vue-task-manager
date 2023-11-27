<template>

<h3>Signup Page</h3>

<div class="form">

    <input type="text" v-model="name" name="name" placeholder="Enter name" id="">
    <input type="email" name="email" v-model="email" placeholder="Enter email" id="">
    <input type="password" name="password" v-model="password" placeholder="Enter password" id=""> <br>
    <button v-on:click="signup">Signup</button>
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
    methods: {
        async signup() {
            console.log("Signup");
            console.log(this.name, this, this.email, this.password);
            let reply = await axios.post("http://localhost:3000/user/", {
                name: this.name,
                email: this.email,
                password: this.password
            });

            if (reply.status == 201) {
                alert("Success!!")
            }
            localStorage.setItem("user", JSON.stringify(reply.data));


        }
    }
}
</script>

<style>
.form{
    width:300px;
    margin:auto;

}
.form input{
    width: 100%; 
    height: 30px; 
    border: 1px solid skyblue; 
    margin-bottom: 20px;
}
.form button {
    width: 100%; 
    background: skyblue; 
    border: none; 
    color: white; 
    height: 30px;
}
</style>