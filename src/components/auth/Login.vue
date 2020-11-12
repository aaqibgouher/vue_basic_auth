<template>
    <div>
        <div class="mt-5"></div>
        <div class="row">
            <div class="col-sm-4 offset-sm-4 border py-5">
                <h3>Login</h3>
                <div class="form-group">
                    <label>Email</label>
                    <input type="email" class="form-control" v-model="email" @keydown.enter="submit">
                </div> 
                <div class="form-group">
                    <label>Password</label>
                    <input :type="getTypeForPassword" class="form-control" v-model="password" @keydown.enter="submit">
                    <input type="checkbox" v-model="show_password"> Show Password
                </div>  
                <div v-if="errors.length">
                    <div class="alert alert-danger" v-for="error in errors" :key="error">{{ error }}</div>
                </div>
                <div class="alert alert-success" v-if="message">{{ message }}</div>
                <button class="btn btn-primary btn-block" @click="submit">{{ login_btn_label }}</button>  
            </div>   
        </div> 
    </div>
</template>

<script>
export default {
    name: "Login",
    data() {
        return {
            errors: [],
            message: "",
            email: "",
            password: "",
            show_password: false,
            login_btn_label: 'Login',
            ADMIN_EMAIL: "admin@gmail.com",
            ADMIN_PASSWORD: "123456"
        }
    },
    methods: {
        validation() {
            this.errors = [];
            if(!this.email) this.errors.push("Email is required.");
            if(!this.password) this.errors.push("Password is required.");
            if(this.password && (this.password.length < 4 || this.password.length > 12)) this.errors.push("Password can be 4-12 char in length");

            return (this.errors.length) ? false : true;
        },
        submit(){
            if(this.validation()){
                this.login_btn_label = "Processing ...";

                if(this.email == this.ADMIN_EMAIL && this.password == this.ADMIN_PASSWORD){
                    this.message = "Successfully login.";
                    localStorage.setItem("login_user_email", this.email);
                    this.email = "";
                    this.password = "";
                    this.$router.push('/');
                }else{
                    this.errors.push("Email/Password is incorrect.")
                }
                this.login_btn_label="Login";
            }
        }
    },
    computed: {
        getTypeForPassword(){
            return this.show_password ? 'text' : 'password';
        }
    }
}
</script>