<template>

  <h1>Kullanıcılar</h1>
  
  <h3>Kayıt Sayısı: {{users.length}}</h3>
  
  <button v-if="users.length == 0" @click="getUsersData()">Kullanıcı Verilerini getir</button>

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

  methods: {
      getUsersData() {

        fetch('https://jsonplaceholder.typicode.com/users')
          .then(async response => {
            this.users = await response.json();
          })

      }
  }

};

</script>