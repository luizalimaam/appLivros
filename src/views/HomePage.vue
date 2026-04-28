<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Meus Livros</ion-title>
        <ion-buttons slot="end">
          <ion-button @click="sair" color="danger">
            <ion-icon slot="icon-only" :icon="logOutOutline"></ion-icon>
          </ion-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding">
      <ion-list>
        <ion-item v-for="livro in livros" :key="livro.id" @click="verDetalhe(livro.id)" button>
          <ion-label>
            <h2>{{ livro.titulo }}</h2>
            <p>{{ livro.autor }}</p>
          </ion-label>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import {
  IonPage, IonHeader, IonToolbar, IonTitle, IonContent,
  IonList, IonItem, IonLabel, IonButton, IonButtons, IonIcon
} from '@ionic/vue'
import { logOutOutline } from 'ionicons/icons'

const livros = ref([
  { id: 1, titulo: 'Dom Casmurro', autor: 'Machado de Assis' },
  { id: 2, titulo: '1984', autor: 'George Orwell' },
  { id: 3, titulo: 'O Pequeno Príncipe', autor: 'Antoine de Saint-Exupéry' }
])

const router = useRouter()

const verDetalhe = (id: number) => {
  router.push(`/book/${id}`)
}

const sair = () => {
  router.push('/login')
}
</script>