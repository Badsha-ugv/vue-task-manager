<template>
<Header/>
<router-view/>

</template>

<script>

// import components
import Header from "./components/Header.vue"
// import Signup from "./components/Signup.vue"

export default {
  name: 'App',
  components: {
    Header,
    // Signup,

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}
/* Global Style */
body{
  padding: 0; 
  margin: 0;
}
button{
  cursor: pointer;
}

/* form global styling  */
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
    cursor: pointer;
}

</style>
