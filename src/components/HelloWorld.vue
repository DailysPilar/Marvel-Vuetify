<template>
  <v-container class="fill-height">
     <v-row>
      <v-col  v-for="n in 9" :key="n" class="d-flex child-flex" cols="3">
        <v-card :disabled="loading" :loading="loading" class="mx-auto pa-2" max-width="300">
          <v-img height="250" width="300" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
          <v-card-item>
           <v-card-title>Cafe Badilico</v-card-title>
           <v-card-subtitle>
             <span class="me-1">Local Favorite</span>
           </v-card-subtitle>
         </v-card-item>
        </v-card>
      </v-col>
     </v-row>
  </v-container>
</template>

<script setup>

</script>
<style scoped>
</style>