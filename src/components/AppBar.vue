<script setup>
import { ref, defineEmits,onMounted} from 'vue'
const seleccion=ref("spiderman")
const emit=defineEmits(['seleccion']);
const enviar=()=>{
  console.log(seleccion.value)
   emit('seleccion', seleccion.value);
}
onMounted(async()=>{
enviar()
})
   

</script>
<template>
<v-bottom-navigation :elevation="9" grow style="background:#FFCDD2;" v-model="seleccion" @click="enviar">
  <v-btn value="spiderman">
    <v-icon>mdi-history</v-icon>

    <span>Spider-Man</span>
  </v-btn>

  <v-btn value="ironman">
    <v-icon>mdi-heart</v-icon>

    <span>Iron-Man</span>
  </v-btn>

  <v-btn value="capitanamerica">
    <v-icon>mdi-map-marker</v-icon>

    <span>Capitán América</span>
  </v-btn>
   <v-btn value="thor">
    <v-icon>mdi-map-marker</v-icon>

    <span>Thor</span>
  </v-btn>
  <v-btn value="hulk">
    <v-icon>mdi-map-marker</v-icon>

    <span>Hulk</span>
  </v-btn>
  <v-btn value="blackwidow">
    <v-icon>mdi-map-marker</v-icon>

    <span>Black Widow</span>
  </v-btn>
  <v-btn value="doctorstrange">
    <v-icon>mdi-map-marker</v-icon>

    <span>Doctor Strange</span>
  </v-btn>
</v-bottom-navigation>
</template>
<style>

</style>