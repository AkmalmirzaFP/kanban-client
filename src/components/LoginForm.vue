<template>
    <div class="container-form-login" >
        <form class="form-login" >
            <div class="mb-3">
                <p style="color: red;" > {{error}}</p>
              <label for="exampleInputEmail1" class="form-label">Email address</label>
              <input type="email" class="form-control" v-model="user.email" id="email-login" aria-describedby="emailHelp">
            </div>
            <div class="mb-3">
              <label for="exampleInputPassword1" class="form-label">Password</label>
              <input type="password" class="form-control" v-model="user.password" id="password-login">
            </div>
            <button type="submit" class="btn btn-primary" @click=" login()">Submit</button><br>
            <g-signin-button :params="googleSignInParams" @success="onSignInSuccess" @error=" onSignInError" class="mt-2" >
                <button type="submit" class="btn btn-primary" >Sign in with Google</button>
            </g-signin-button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'LoginForm',
    data(){
        return{
            user:{
                email: '',
                password: ''
            },
            googleSignInParams: {
                client_id: '796724939555-b3h495ls02tk9lgi7o4md59f9sabc02l.apps.googleusercontent.com'
            }
            
        }
    },
    props: ['error'],
    methods:{
        login(){
            this.$emit('login', this.user)
            this.$emit('auth')
        }, 
        onSignInSuccess(googleUser){
            this.$emit('success', googleUser)
        },
        onSignInError(googleUser){
            this.$emit('error', googleUser)
        }
    }
}
</script>

<style>

</style>