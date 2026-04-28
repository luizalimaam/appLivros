<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Detalhes do Livro</ion-title>
        <ion-buttons slot="start">
          <ion-back-button default-href="/home"></ion-back-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding">
      <div v-if="livro">
        <h1>{{ livro.titulo }}</h1>
        <h3>{{ livro.autor }}</h3>
        <p>{{ livro.descricao }}</p>
      </div>
      <p v-else>Livro não encontrado</p>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButtons, IonBackButton } from '@ionic/vue'

const livros = [
  { id: 1, titulo: 'Dom Casmurro', autor: 'Machado de Assis', descricao: 'A obra-prima de Machado de Assis conta a história de Bentinho e Capitu.' },
  { id: 2, titulo: '1984', autor: 'George Orwell', descricao: 'Um clássico da literatura distópica sobre vigilância.' },
  { id: 3, titulo: 'O Pequeno Príncipe', autor: 'Antoine de Saint-Exupéry', descricao: 'Uma história filosófica sobre amizade e amor.' }
]

const route = useRoute()
const livro = ref<any>(null)

onMounted(() => {
  const id = Number(route.params.id)
  livro.value = livros.find(l => l.id === id)
})
</script>

<style scoped>
h1 {
  color: var(--ion-color-primary);
}
h3 {
  color: var(--ion-color-medium);
}
p {
  line-height: 1.6;
}
</style>