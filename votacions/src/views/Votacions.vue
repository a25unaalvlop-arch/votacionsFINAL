<script setup>
import { onMounted } from 'vue';
import { ref } from 'vue'
import { useAppStore } from '../stores/app.js';
import { useRouter } from 'vue-router'
import botoVotar from '../components/botoVotar.vue';
import ChartComponent from '../components/ChartComponent.vue';
const route = useRouter()
const appStore = useAppStore()
const options = ref(['Green', 'Red', 'Blue', 'Purple']);

import WebSocketService from '@/services/WebSocketService';
let wsService;

onMounted(() => {
  if (appStore.isLoggedIn == false) {
    alert("No has fet login!")
    route.push('/')
  }
})

onMounted(() => {
  if (appStore.isLoggedIn == false) {
    alert("No has fet login!")
    route.push('/')
  }
  // Engengo el servei de websockets amb el port que tinc configurat al docker compose
  wsService = new WebSocketService('ws://localhost:3000');
  wsService.connect();
})

function gestioVot(id) {
  console.log("vot")
  if (id !== -1 && wsService) {
    console.log('Vot enviat a ' + id)
    wsService.sendVote(id);
  }
}

</script>


<template>
  <div>
    <v-row>
      <v-col v-for="(actual, index) in options" :key="index" cols="12" sm="6" md="3">
        <botoVotar :voteCount="appStore.votos[index]" :idOption="index" @votar="gestioVot"
          :style="{ backgroundColor: options[index] }">
          {{ actual }}
        </botoVotar>
      </v-col>
    </v-row>
  </div>
  <div>
    <ChartComponent />
  </div>
</template>
