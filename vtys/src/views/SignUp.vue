<template>
    <div class="SignUp">
        <form @submit.prevent="handleSubmit">
            <h1 class="giris">Sign Up</h1>
            <div>
                <label>Ad <span id="yildiz">*</span></label>
                <input id="text" type="isim" required v-model="isim" placeholder="Enter your name">
                <label>Soyad <span id="yildiz">*</span></label>
                <input id="text" type="soyisim" required v-model="soyisim" placeholder="Enter your surname">
                <label>E-mail<span id="yildiz"> * </span></label>
                <input id="text" type="email" required v-model="email" placeholder="Enter your E-mail">
                <label>Kullanici Adi<span id="yildiz">*</span></label>
                <input id="text" type="userid" required v-model="userid" placeholder="Enter your User ID">
                <label>Password <span id="yildiz">*</span><span id="uyari" v-if="this.passwordError">{{ passwordError }}</span></label>
                <input id="text" type="password" required v-model="password" placeholder="Enter your password here">                
                <label>Password Confirmation <span id="yildiz">*</span><span id="uyari" v-if="this.passwordconfirm">Şifreler Eşleşmiyor</span></label>
                <input id="text" type="password" required v-model="confirmpassword" placeholder="Confirm your password">
                <label>Telefon Numarasi<span id="yildiz">*</span></label>
                <input id="text" type="phone" required v-model="phone" placeholder="Enter your Phone Number">
                <button>Sign Up</button>
            </div>
            <button @click="$router.push('/')">Already have an account?</button>

        </form>
    </div>
<p>Ad-Soyad: {{ isim }} {{ soyisim }}</p>
<p>E-mail: {{email}}</p>
<p>User ID: {{userid}}</p>
<p>Password: {{password}}</p>
<p>Confim Password: {{ confirmpassword }}</p>
<p>Phone: {{ phone }}</p>
</template>


<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            userid: '',
            isim:'',
            soyisim:'',
            passwordError: '',
            phone:'',
            confirmpassword:'',
            passwordconfirm:false
        }
    },
    methods: {
        handleSubmit() {
            // Validate password
            if (this.password.length > 5) {
                this.passwordError = ''
            }
            else {
                this.passwordError = 'Password must be at least 6 chars long'
            }
            if (this.password === this.confirmpassword){
                this.passwordconfirm = false
            }
            else{
                this.passwordconfirm = true;
            }
            if (!this.passwordError) {
                console.log('email: ', this.email)
                console.log('password: ', this.password)
                console.log('User ID: ', this.userid)
                console.log('Name: ', this.isim)
                console.log('Surname: ', this.soyisim)
                console.log('Phone: ', this.phone)
            }
        }
    }
}
</script>


<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
    background-color: rgba(36, 34, 34, 0.5)
}

button {
    background: #0b6dff;
    border: 0;
    width:100%;
    margin-left:auto;
    margin-right:auto;
    padding: 10px 20px;
    color: white;
    border-radius: 20px;
    cursor: pointer;
}

.submit {
    text-align: center;
}

label {
    color: black;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.7em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}

input[id="text"] {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px white;
    color: black;
    background-color: #d3d3d3;
    cursor: auto;
}

div[class="SignUp"] {
    margin: auto;
}

#yildiz {
    color: red;
    font-size: 15px;
}
#uyari{
    text-align: left;
    font-style: bold;
    font-size: 20px;
}
input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
    cursor: pointer;
}

.pill {
    display: inline-block;
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

h1.giris {
    margin: auto;
    text-align: center;
    color: black;
}

</style>