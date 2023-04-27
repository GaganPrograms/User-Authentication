<template>
    <div>
      
      <form @submit.prevent="register">
        <h1>Register</h1>
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="formData.name" required>
  
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="formData.email">
  
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="formData.password">

        <label for="dateOfBirth">DOB:</label>
        <input type="dateOfBirth" id="dateOfBirth" v-model="formData.dateOfBirth">
  
        <button type="submit">Register</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    
    data() {
      return {
        formData: {
            name: "",
            email: "",
            password: "",
            dateOfBirth: ""
      }
      }
    },
    methods: {
     async register() {
        try {
        const response = await this.$axios.$post('http://localhost:5500/user/signup', this.formData)
        console.log(response)

        // redirect to profile page
       if(response.status === "SUCCESS"){
        this.$router.push('/login')
       }else if(response.status === "FAILED"){
        alert(response.message)
       }
        
      } catch (error) {
        console.error(error)
      }
      }
    }
  }
  </script>
  <style >
  .register {
    width: 100px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-family: Arial, sans-serif;
  }
  
  h1 {
    font-size: 24px;
    margin-top: 0;
  }
  
  label {
    display: block;
    margin-top: 10px;
    font-size: 16px;
  }
  
  input {
    width: 500px;
    padding: 8px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-sizing: border-box;
    margin-top: 5px;
  }
  
  button {
    display: block;
    margin-top: 20px;
    background-color: #31af4a;
    color: #ffffff;
    border: none;
    border-radius: 20px;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #17ea48;
  }
  
  button:active {
    background-color: #2ae334;
  }
  
  button:focus {
    outline: none;
  }

  div{
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 90vh;
  }
  body{
    background: #3d3b47;
  }

  form{
    padding:40px;
    background: #ffffff;
    width: 500px;
    border-radius: 30px
  }
  </style>
