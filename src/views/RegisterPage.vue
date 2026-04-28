<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Cadastro</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding">
      <ion-item>
        <ion-label position="floating">Nome</ion-label>
        <ion-input v-model="nome"></ion-input>
      </ion-item>

      <ion-item>
        <ion-label position="floating">E-mail</ion-label>
        <ion-input type="email" v-model="email"></ion-input>
      </ion-item>

      <ion-item>
        <ion-label position="floating">Senha</ion-label>
        <ion-input type="password" v-model="senha"></ion-input>
      </ion-item>

      <ion-item>
        <ion-label position="floating">Confirmar Senha</ion-label>
        <ion-input type="password" v-model="confirmarSenha"></ion-input>
      </ion-item>

      <ion-button expand="block" @click="cadastrar">Cadastrar</ion-button>
      <ion-button fill="clear" @click="irParaLogin">Já tenho conta</ion-button>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonItem, IonLabel, IonInput, IonButton } from '@ionic/vue'

const nome = ref('')
const email = ref('')
const senha = ref('')
const confirmarSenha = ref('')
const router = useRouter()

const cadastrar = () => {
  if (!nome.value || !email.value || !senha.value || !confirmarSenha.value) {
    alert('Preencha todos os campos')
    return
  }
  if (senha.value !== confirmarSenha.value) {
    alert('Senhas não conferem')
    return
  }
  alert('Cadastro realizado com sucesso!')
  router.push('/login')
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