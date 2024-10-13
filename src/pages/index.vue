<template>
<v-app>
      <AppBar @seleccion="recibir"></AppBar>
    <v-main>
      <HelloWorld v-if="personaje" :personaje="personaje"/>
    </v-main>
  </v-app>
</template>

<script setup>
import {ref} from 'vue'
const personaje=ref("")
const recibir=(valor)=>{
  console.log(valor)
  personaje.value=valor
}
</script>
