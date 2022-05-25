<template>
<form v-on:submit.prevent="submitForm">
  <div>
    <label for="username">id: </label>
    <input id="username" type="text" v-model="username">
  </div>
  <div>
  <label for="password">pw: </label>
    <input id="password" type="password" v-model="password">
  </div>
  <button type="submit">login</button>
</form>
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return{
      username:'',
      password:''
    }
  },
  methods: {
    submitForm(){
      var url = 'https://jsonplaceholder.typicode.com/users'      
      var data={
        username:this.username,
        password:this.password
      }
      axios.post(url, data).
      then((r) =>{
        console.log(r)
      }).
      catch((e) =>{
        console.log(e)
      })
    }
  },
}
</script>

<style>
</style>
