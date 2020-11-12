<template>
    <div>
        <BlogApp/>
    </div>
</template>

<script>
import BlogApp from './blog/BlogApp';

export default {
    name: "Home",
    components: {
        BlogApp
    },
    data() {
        return {

        }
    },
    created() {
        this.checkLogin();
    },
    methods: {
        checkLogin(){
            if(!localStorage.getItem("login_user_email")){
                // redirect
                this.$router.push('login');
            }
        }
    }
}
</script>