<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Login</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding">
      <ion-item>
        <ion-label position="floating">E-mail</ion-label>
        <ion-input type="email" v-model="email"></ion-input>
      </ion-item>

      <ion-item>
        <ion-label position="floating">Senha</ion-label>
        <ion-input type="password" v-model="senha"></ion-input>
      </ion-item>

      <ion-button expand="block" @click="fazerLogin">Entrar</ion-button>
      <ion-button fill="clear" @click="irParaCadastro">Criar conta</ion-button>
      <ion-button fill="clear" @click="irParaRecuperarSenha">Esqueceu a senha?</ion-button>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonItem, IonLabel, IonInput, IonButton } from '@ionic/vue'

const email = ref('')
const senha = ref('')
const router = useRouter()

const fazerLogin = () => {
  if (email.value && senha.value) {
    router.push('/home')
  } else {
    alert('Preencha e-mail e senha')
  }
}

const irParaCadastro = () => router.push('/register')
const irParaRecuperarSenha = () => router.push('/forgot-password')
</script>

<style scoped>
ion-item {
  margin-bottom: 15px;
}
ion-button {
  margin-top: 15px;
}
</style>