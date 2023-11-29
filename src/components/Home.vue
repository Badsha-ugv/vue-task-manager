<template>

    <h3>Welcome Home, Hello {{userName}} </h3>
</template>

<script>


export default {
    name: 'HomeComp',
    data() {
        return {
            userName: '',
        };
    },

    mounted() {
        let user = localStorage.getItem('user');
        
        if (!user) {
            this.$router.push({ name: "Signup" });
        } else {
            this.userName= JSON.parse(user).name;
        }
        
    },
    
}
</script>

