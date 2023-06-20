<template>
<div class="background">
      <!-- <div class="header"> -->
        <div class="navbar">
        <a href="https://student.v-learning.in/"><img src="../src/assets/logolink.webp" class="image"></a>
           <div class="nav">
          <button type="button" class="button1">
            <span>SignUp</span>
          </button>
          <button type="button" class="button2">
            <span>Login</span>
          </button>
        </div>
        </div>
        <div class="patch">
        <div class="login">
      <img src="../src/assets/03.png" class="imglay">
      <form @submit.prevent="submitForm">
    <div>
      <label for="email">Email:</label>
      <input type="email" id="email" v-model="email" />
      <small v-if="errors.email" class="err1">{{ errors.email }}</small>
    </div>
    <div>
    <label for="password">Password:</label>
    <div class="password-input">
      <input type="password" id="password" v-model="password"/>
      <small v-if="errors.password" class="err2">{{ errors.password }}</small>
    </div>
  </div>
    <button type="submit">Login</button>
  </form>
  </div>
  </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      errors: {
        email: '',
        password: '',
        showPassword: false,
      },
    };
  },
  methods: {
    submitForm() {
      this.errors = {}; // Clear previous errors

      if (!this.email) {
        this.errors.email = 'Email is required';
      } else if (!this.isValidEmail(this.email)) {
        this.errors.email = 'Email is not valid';
      }

      if (!this.password) {
        this.errors.password = 'Password is required';
      } 
      else if (this.password.length < 6) {
        this.errors.password = 'Password must be at least 6 characters';
      }     
      if (Object.keys(this.errors).length === 0) {
        // Perform signup logic or submit the form
        alert('Login successful');
        // Reset form fields
        this.email = '';
        this.password = '';
      }
    },
    isValidEmail(email) {
      // Implement your email validation logic here
      const re = /^[\w-]+(\.[\w-]+)*@([\w-]+\.)+[a-zA-Z]{2,7}$/;
      return re.test(email);
    },
  },
};
</script>

<style scoped>
.signup-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.err1{
  color:red;
}
form {
  width: 400px;
  padding: 75px;
  background-color: white;
  border-radius: 4px;
  margin-top: -1rem;
}
.err2{
  color:red
}
.form-group {
  margin-bottom: 20px;
  border-radius: 3rem;
}

label {
  display: block;
  font-weight: 600;
  margin-bottom: 10px;
}

input[type="text"],
input[type="firstname"],
input[type="email"],
input[type="password"],
input[type="passwordConfirm"]
{
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border-radius: 15px;
  font-style: Poppins;
  border: 1px solid lightgray;
}

button[type="submit"] {
  width: 85%;
    padding: 10px;
    background-color: blue;
    color: white;
    border: none;
    border-radius: 19px;
    font-size: 16px;
    font-weight: 600;
    margin-top: 11px;
    margin-left: 36px;
    cursor: pointer;
}

.form-control {
  margin-bottom: 10px;
}

.error {
  border-color: red;
}

.small {
  color: red;
  font-size: 12px;
}

.password-input {
  position: relative;
}

.hide-password {
    border-radius: 3rem;
    width: 16rem;
    border: none;
    font-size: 2rem;
    height: 2rem;
    line-height: 5rem;
    margin-top: -1rem;
    margin-left: 127px;
}

.password-input button {
    position: absolute;
    top: -9px;
    color: #51d330;
    right: -50px;
    border-radius: 12px;
}
.background{
  width: 100%;
    min-height: 100vh;
    overflow: hidden;
    padding: 5rem;
    max-width: 1200px;
    margin: 0 auto;
    background: #f4faff;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
.image {
    height: 100%;
    width: 15%;
}
  .login {
    display: flex;
    flex-direction: row;
    height: 79%;
    background: #efefef;
    border-radius: 12px;
}
.email{
    border-radius: 3rem;
    width: 16rem;
    border: none;
    font-size: 2rem;
    height: 2rem;
    line-height: 5rem;
    margin-top: 106px;
    margin-left: 85px;
}
.button1 {
    color: #3d68c9;
    font-weight: 600;
    font-size: 11px;
    width: 94px;
    margin-left: 1rem;
    height: 25px;
    border: solid 1px #0b59a5;
    border-radius: 3rem;
    padding: -14rem 0rem;
    /* padding: 2rem 5rem; */
    text-decoration: none;
    background: rgba(0,0,0,0);
    transition: 0.50s;
}
.button2 {
    color: #3d68c9;
    font-weight: 600;
    font-size: 11px;
    width: 94px;
    margin-left: 1rem;
    height: 25px;
    border: solid 1px #0a4987;
    border-radius: 3rem;
    padding: -14rem 0rem;
    /* padding: 2rem 5rem; */
    text-decoration: none;
    background: rgba(0,0,0,0);
    transition: 0.50s;
}
.imglay{
  width: 50%;
}
.nav {
    display: flex;
    margin-left: 47rem;
    position: absolute;
}
.patch {
    width: 76%;
    margin-left: 7px;
    min-height: 75vh;
    padding: 2rem;
    margin: 1rem 4px;
    border-radius: 1rem;
    background: #fff;
    box-shadow: -5px 10px 15px rgba(11,89,165,.2);
}
.error {
  color: red;
  margin-top: 10px;
}
.navbar{
    display: flex;
    justify-content: space-between;
    align-items: center;
    text-align: center;
}

.button1:hover,.button2:hover{
  background-color: blue;
  color: white;
}
</style>
