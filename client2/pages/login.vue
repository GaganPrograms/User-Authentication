<template>
    <div>
      
      <form>
        <h2>Login</h2>
        <label for="email">Email:</label>
        <input type="text" id="email" v-model="formData.email">
        <br>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="formData.password">
        <br>
        <button @click.prevent="login">Login</button>
        <nLink to="/register">Register</nLink>
        
      </form>
    </div>
  </template>
  
  <script>
  export default {
    props: ['formData.email'],
    data() {
      return {
        formData: {
        email: '',
        password: ''
      }
      }
    },
    methods: {
        // login function
     async login() {
          
          try {
        const response = await this.$axios.$post('http://localhost:5500/user/signin', this.formData)
        console.log(response)

        // redirect to profile page
        if(response.status === 'SUCCESS'){
            localStorage.setItem('token', response.token);
            this.$router.push('/profile')
        } else if(response.status === "FAILED"){
            alert(response.message)
            // this.$router.push('/register')
        } 
        // else if(response.message === 'user does not exist'){
        //     alert("register first")
        //     this.$router.push('/register')
        // }
        
      } catch (error) {
        console.error(error)
      }
        // Send login request to server using this.username and this.password
        // If login successful, redirect to user dashboard
        // If login fails, display error message
      }
    }
  }
  </script>
  <style>
  body{
    background: #3d3b47;
  }
  /* Remove default margin and padding from form elements */
  form {
    padding:40px;
    background: #ffffff;
    width: 500px;
    border-radius: 30px
  }
  
  /* Set font size and line height for labels and inputs */
  label, input[type="text"], input[type="password"], button {
    font-size: 16px;
    line-height: 1.5;
  }
  
  /* Set width and margin for inputs */
  input[type="text"], input[type="password"] {
    width: 100%;
    margin-bottom: 10px;
  }
  
  /* Set button color and hover effect */
  button {
    background-color: #41ae65;
    color: #fff;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 20px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #0dd839;
  }
  
  /* Center form horizontally */
  div {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 70vh;
    
    
  }
  
  
  form {
    width: 300px;
  }

  .h2 {
    text-align: center;
    margin-top: 0;
    margin-bottom: 20px;
  }

 </style>