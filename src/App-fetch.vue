<template>
  <h1>Kullanıcılar</h1>
  
  <ul>
    <li v-for="user in users">
      {{user.name}}
    </li>  
  </ul>
  

</template>

<script>
import { ref } from "vue";

export default {
  name: "App",
  data(){
    return {
      users: []
    }
  },

  created() {

      fetch('https://jsonplaceholder.typicode.com/users')
        .then(async response => {
          this.users = await response.json();
        })
        .catch(error => {
          this.errorMessage = error;
          console.error("There was an error!", error);
        });
        
    }  

};

</script>