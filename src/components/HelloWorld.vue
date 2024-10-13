<template>
  <v-container class="fill-height">
     <v-row>
      <v-col  v-for="(n,index) in arreglo" :key="index" class="d-flex child-flex" cols="3">
        <v-card class="mx-auto pa-2" max-width="300">
          <v-img height="250" width="300" :src="n.images.original.url"></v-img>
          <v-card-item>
           <v-card-title>{{n.type}}</v-card-title>
           <v-card-subtitle >
             <span class="me-1">{{n.title}}</span>
           </v-card-subtitle>
        
         </v-card-item>
        </v-card>
      </v-col>
     </v-row>
  </v-container>
</template>

<script setup>
import {onMounted,ref,watch } from 'vue'
const props=defineProps(['personaje']);
 const objeto=ref(null);
 const error=ref(null);
 const arreglo=ref([]);

const consumirapi=async()=>{
    try {
    const data=await fetch(`https://api.giphy.com/v1/gifs/search?limit=20&q=${props.personaje}&api_key=Gfrx20EGDvpUzUzUbuqw2crJQhfT4cSl`);
    if(!data.ok){
        throw Error("Datos no validos");
    }
    objeto.value=await data.json();
    console.log(objeto.value)
    } catch (err) {
        error.value=err.message;
    
     }
    arreglo.value=objeto.value.data
}
onMounted(consumirapi)
watch(() => props.personaje,consumirapi )
</script>
<style scoped>
</style>