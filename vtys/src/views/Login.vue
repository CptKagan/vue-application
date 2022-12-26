<template>
    <div class="Login" >
    <br><br><br><br><br><br><br><br>
    
<form @submit.prevent="handleSubmit">
    <h1 class="giris">Login</h1>
    <div>
        <label>E-mail<span id="yildiz"> * </span></label>
        <input id="text" type="email" required v-model="email" placeholder="E-mail / Phone number / UserID">
        <label>Password <span id="yildiz">*</span><span id="uyari" v-if="this.passwordError">{{ passwordError }}</span></label>
        <input id="text" type="password" required v-model="password" placeholder="Enter your password here">
    </div>

    <div>
        <label v-if="alert" style="color:crimson">Kullanıcı adı veya Şifre Yanlış!</label>
       <button @click="logincheck(this.email, this.password)">Login</button>
        <button @click="$router.push('/forgotpassword')">Forgot your password?</button>
        <button @click="$router.push('/signup')">Sign Up!</button>
    </div>


</form>
    </div>
<!-- <p>User ID: {{userid}}</p>
<p>E-mail: {{email}}</p>
<p>Password: {{password}}</p>
<p>Role: {{role}}</p>
<p>Terms accepted: {{terms}}</p> -->
</template>


<script>
import router from '@/router'
    export default {
        data(){
            return {
                email: '',
                password: '',
                userid:'',
                passwordError:'',
                islogged:false,
                alert:false
            }
        },
        methods: {
            handleSubmit(){
                // Validate password
                if(this.password.length > 5){
                    this.passwordError = ''
                }
                else{
                    this.passwordError = 'Password must be at least 6 chars long'
                }
                if(!this.passwordError){
                    console.log('email: ', this.email)
                    console.log('password: ', this.password)
                }
            },
            logincheck(eposta, sifre){
                if (eposta == 'flowerybeggar@gmail.com' && sifre == '315231'){
                    this.islogged = true;
                    if(this.islogged==true){
                        console.log('user logged in')
                        router.push('/mudurpanel')
                    }
                }
                else{
                    this.alert=true;
                }
            }
        }
    }
</script>


<style>
form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
    background-color: rgba(36, 34, 34, 0.5)
}
button{
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top:20px;
    color: white;
    border-radius: 20px;
    cursor:pointer;
}
.submit{
    text-align:center;
}
label{
    color: black;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.7em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input[id="text"]{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px white;
    color: black;
    background-color:#d3d3d3;
    cursor: auto;
}
div[class="Login"]{
    margin: auto;
}
#yildiz{
    color: red;
    font-size: 15px;
}
#uyari {
    text-align: left;
    font-style: bold;
    font-size: 20px;
}
input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
    cursor: pointer;
}
.pill{
    display:inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}
h1.giris{
    margin: auto;
    text-align: center;
    color: black;
}
</style>