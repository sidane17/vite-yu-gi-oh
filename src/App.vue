<script >

import AppHeader from './components/AppHeader.vue';
import store from './data/store.js';
export default {
  components: {
    AppHeader,
  },data(){
    return{
      store
    }
  },
  mounted(){
     axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0").then(risultato=>{
      this.store.dati=risultato.data.data
      
      console.log(this.store.dati)
    })
  
  }
}
  

</script>

<template>

<div class="w-100">
<select name="" id="">
  <option v-for="(elemento) in this.store.dati" :value="elemento.archetype">{{ elemento.archetype }}</option>
</select>  <button @click="getPersonaggi">Cerca</button>
</div>
<div class="container_card">
<div v-for="(elemento) in this.store.dati" class="card">
<img :src="elemento.card_images[0].image_url" alt="">

<span></span>
</div>
</div>
</template>

<style scoped>
.container_card{
  background-color: white;
  width: 80rem;
  height: 100vh;


  display: flex;
  flex-wrap: wrap;
  overflow: scroll;
}
.card{
  height: fit-content;
  width: calc(100%/5);
    border-style: dashed;
}
img{
  width: 100%;
}
</style>
