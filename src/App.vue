<template>

  <h1>Kullanıcılar</h1>

  <button  @click="getUsersData('SÜRÜCÜ')">Sürücüleri Getir</button>
  <button  @click="getUsersData('ARAÇ')">Araçları Getir</button>

  <div v-if="suruculer.length > 0">
    <h2>Sürücülerimiz ({{suruculer.length}} KİŞİ):</h2>
    <ul>
      <li v-for="surucu in suruculer">
        {{surucu.adsoyad.toLowerCase().split('').reverse().join('')}}
      </li>  
    </ul>
  </div>

  <div v-if="araclar.length > 0">
    <h2>Araçlarımız  ({{araclar.length}} ARAÇ):</h2>
    <ul>
      <li v-for="arac in araclar">
        {{arac.plaka}}
      </li>  
    </ul>
  </div>

</template>

<script>
import { ref } from "vue";

export default {
  name: "App",
  data(){
    return {
      suruculer: [],
      araclar: []
    }
  },

  methods: {

      // DUMY DATA İÇİN: https://jsonplaceholder.typicode.com/

      getUsersData(veriKaynagi) {
        if(veriKaynagi == "SÜRÜCÜ") {
          fetch('http://localhost/YAKIT2/data.fabrika.php?islem=suruculer')
            .then(async response => {
              this.suruculer = await response.json();
              this.araclar = []
            })
        }

        if(veriKaynagi == "ARAÇ") {
          fetch('http://localhost/YAKIT2/data.fabrika.php?islem=araclar')
            .then(async response => {
              this.araclar = await response.json();
              this.suruculer = []
            })
        }

      }
  }

};

</script>