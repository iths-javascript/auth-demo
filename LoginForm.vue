<template>
<form @submit.prevent="submit">
  <input type="text" v-model="email" placeholder="email">
  <input type="text" v-model="password" placeholder="password">
  <button>Login</button>
</form>
</template>

<script>
import axios from 'axios'

export default {
  
  data(){return{
    email: 'customer@example.com',
    password: 'password'
  }},

  methods:{
    async submit(){
      const payload = {email: this.email, password: this.password}
      
      const responseData = await axios.post('http://localhost:5000/api/auth', payload)
  
      // const request = await fetch('http://localhost:5000/api/auth', {
      //   method: 'POST',
      //   headers: {
      //     'Content-Type': 'application/json'
      //   },
      //   body: JSON.stringify(payload)
      // })

      // const responseData = await request.json()      

      this.$emit('login', responseData)
    }
  }
}
</script>

<style>
form{
  max-width: 250px;
  box-shadow: 0px 2px 5px -1px rgba(0,0,0,0.75);
  padding: 1rem 3rem;
  margin: auto;
  margin-top: 10rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  transform: scale(2);
}
form input{
  margin: 1rem 2rem;
  padding : 0.5rem;
  border-radius: 6px;
  border: 1px solid grey;
  outline: none;
  width: 100%;
}
form input:first-of-type{
  margin-bottom: 0;
}

button{
  align-self: flex-end;
  outline: none;
  border: 0;
  font-size: 1.2rem;
  color: beige;
  padding: 0.5rem 1rem;
  background-color: skyblue;
  position: relative;
  right: -2rem;
  transition: background-color 0.1s transform 0.1s;
  cursor: pointer;
}


button:hover{
  background-color: rgb(60,80,140);
}
button:active{
  background-color: rgb(30,50,120);
  transform: scale(0.9);
}
</style>