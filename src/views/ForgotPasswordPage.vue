<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Recuperar Senha</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding">
      <ion-item>
        <ion-label position="floating">E-mail</ion-label>
        <ion-input type="email" v-model="email"></ion-input>
      </ion-item>

      <ion-button expand="block" @click="recuperar">Recuperar Senha</ion-button>
      <ion-button fill="clear" @click="irParaLogin">Voltar ao login</ion-button>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonItem, IonLabel, IonInput, IonButton } from '@ionic/vue'

const email = ref('')
const router = useRouter()

const recuperar = () => {
  if (email.value) {
    alert(`E-mail de recuperação enviado para ${email.value}`)
    router.push('/login')
  } else {
    alert('Digite seu e-mail')
  }
}

const irParaLogin = () => router.push('/login')
</script>

<style scoped>
ion-item {
  margin-bottom: 15px;
}
ion-button {
  margin-top: 15px;
}
</style>