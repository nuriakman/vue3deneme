<template>
  <h1>{{isim}}</h1>
</template>

<script>
import { ref } from "vue";

export default {
  name: "App",
  data(){
    return {
      isim: "Nuri Akman 123",
    }
  }
};

</script>