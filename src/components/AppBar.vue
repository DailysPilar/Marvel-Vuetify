<script setup>
import { ref ,onMounted} from 'vue'
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
    <v-icon >mdi-spider</v-icon>

    <span>Spider-Man</span>
  </v-btn>

  <v-btn value="ironman">
    <v-icon>mdi-robot</v-icon>

    <span>Iron-Man</span>
  </v-btn>

   <v-btn value="thor">
    <v-icon>mdi-gavel</v-icon>

    <span>Thor</span>
  </v-btn>
  <v-btn value="hulk">
    <v-icon>mdi-foot-print</v-icon>

    <span>Hulk</span>
  </v-btn>
  <v-btn value="doctorstrange">
    <v-icon>mdi-magic-staff</v-icon>

    <span>Doctor Strange</span>
  </v-btn>
</v-bottom-navigation>
</template>
<style>

</style>