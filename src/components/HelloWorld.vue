<template>
  <v-container class="fill-height">
    <v-responsive
      class="align-center fill-height mx-auto"
      max-width="900"
    >
      <div class="text-center">
        <v-avatar image="@/assets/R.jpeg" size="150" class="mb-4"></v-avatar>
        <h1 class="text-h3 font-weight-bold">To-Do List</h1>
        
      </div>

      <v-text-field class="mt-4 mx-auto"
        rounded="xl"
        hide-details="true"
        append-inner-icon="mdi-plus"
        density="compact"
        label="Add new task"
        variant="solo"
        max-width="600"
        
      ></v-text-field>
      <div class="py-4" />
<v-row justify="space-between">
  <v-col cols="12" v-for="(x,index) in arreglo" :key="index">
    <v-card color="surface-variant" rounded="xl" variant="outlined" class="d-flex align-center" style="height: 40px;padding:20px;">
      <v-icon icon="mdi-check-circle-outline" class="mr-4"></v-icon>
      <v-spacer></v-spacer>
      <div class="text-center flex-grow-1">{{x}}</div>
      <v-spacer></v-spacer>
      <v-icon icon="mdi-pencil" class="ml-4"></v-icon>
      <v-icon icon="mdi-delete" class="ml-2"></v-icon>
      <v-icon icon="mdi-star" class="ml-2"></v-icon>
    </v-card>
  </v-col>
</v-row>

    </v-responsive>
  </v-container>
</template>

<script setup>
import {ref} from 'vue'
const arreglo =ref(['a','s','d','f','g','r','d','w'])
</script>
