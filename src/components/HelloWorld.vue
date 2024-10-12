<template>
  <v-container class="fill-height">
    <v-responsive
      class="align-start fill-height mx-auto"
      max-width="700">
      <div class="text-center">
        <v-avatar image="@/assets/R.jpeg" size="100" class="mb-4"></v-avatar>
        <h1 class="text-h5 font-weight-bold">To-Do List</h1>
      </div>
      <v-text-field class="mt-4 mx-auto custom-icon"
        rounded="xl"
        single-line
        hide-details="true"
        append-inner-icon="mdi-plus"
        density="compact"
        label="Add new task"
        variant="solo"
        max-width="500"
        @click:append-inner="agregartarea"
        v-model="nuevatarea.tarea"
        maxlength="60">
      </v-text-field>
      <div class="py-2" />
      <v-sheet 
    class="d-flex align-start justify-center flex-wrap  px-20"
    elevation="8"
    min-height="400"
    max-width="800"
    width="100%"
    height="100%"
    rounded="xl"
   
  >
   
  <div v-if="arreglo.length === 0" class="d-flex align-center justify-center " style="width: 100%; height: 100%;margin-top:50px">
    <h2 class="text-h7 mb-6" style="color:#757575;">No task</h2>
  </div>

<v-row justify="space-between" class="mt-4 mb-10">
  <v-col cols="12" v-for="(x,index) in arreglo" :key="index">
    <v-card color="surface-variant" rounded="xl" variant="outlined" class="d-flex align-center mx-10" style="height: 40px;padding:20px;">
      <v-icon icon="mdi-check-circle-outline" class="mr-4" role="button" :color="x.lista ? '#64DD17':'white'" @click="cambiarestatus(index)"></v-icon>
      <v-spacer></v-spacer>
      <div class="text-center flex-grow-1" :style="{textDecoration:x.lista?'line-through':'none'}">{{x.tarea}}</div>
      <v-spacer></v-spacer>
      <v-icon icon="mdi-pencil" color="white" class="ml-4" role="button" :disabled="x.lista" @click="editartarea(index)"></v-icon>
      <v-icon icon="mdi-delete" color="white" class="ml-2" role="button" :disabled="x.lista" @click="eliminartarea(index)"></v-icon>
      <v-icon icon="mdi-star" class="ml-2" role="button" :disabled="x.lista" :color="x.esfavorito ? '#FFFF00':'white'" @click="cambiarfavorito(index)"></v-icon>
    
    </v-card>
    <v-bottom-sheet v-model="editar" inset>
        <v-card
        class="text-center"
        height="200">
        <v-card-text>
          <v-btn
            variant="outlined"
            color="yellow"
            @click="ocultar"
          >
            Ok
          </v-btn>
          <br>
          <br>
          <v-textarea maxlength="60" class="mx-2" rows="1" no-resize label="" variant="solo-filled" v-model="x.tarea"></v-textarea>
        </v-card-text>
      </v-card>
    </v-bottom-sheet>
  </v-col>
</v-row></v-sheet>
<v-bottom-sheet v-model="existente" inset>
      <v-card
        class="text-center"
        height="150">
        <v-card-text>
          <v-btn
            variant="outlined"
            color="yellow"
            @click="existente = !existente"
          >
            Ok
          </v-btn>
          <br>
          <br>
          <div>
           Existing task
          </div>
        </v-card-text>
      </v-card>
    </v-bottom-sheet>

    </v-responsive>
  </v-container>
</template>

<script setup>
import {ref} from 'vue'
const arreglo =ref([])
const existente=ref(false)
const nuevatarea=ref({
  tarea:"",
  esfavorito:false,
  lista:false,
})
const editar=ref(false)
const limpiartarea=()=>{
  nuevatarea.value={
    tarea:"",
    esfavorito:false,
    lista:false,
   }
}
const agregartarea=()=>{
  if(!(nuevatarea.value.tarea==="" || arreglo.value.includes(nuevatarea.value))){
   arreglo.value = [...arreglo.value, nuevatarea.value];
   limpiartarea()
 
  }else{
     if(arreglo.value.includes(nuevatarea.value)){
      existente.value=true
      }
     limpiartarea()
  }

}
const cambiarestatus=(indice)=>{
  arreglo.value[indice].lista=!arreglo.value[indice].lista
}
const cambiarfavorito=(indice)=>{
  arreglo.value[indice].esfavorito=!arreglo.value[indice].esfavorito
}
const eliminartarea=(indice)=>{
  arreglo.value.splice(indice,1)
}
const editartarea=(indice)=>{
editar.value=true
}
const ocultar=()=>{
editar.value=false
}
</script>
<style scoped>
.custom-icon :deep(.v-icon) {
  color: yellow; 
}
</style>