<template>
  <section class="p-5">
    <header>
      <h2 class="text-xl font-bold text-center">Consiga notificar o seu cliente</h2>
      <p>É possível pedir sua localização. Se você aceitou quando a página abrir</p>
      isSupported {{ isSupported }}
    </header>
    <div class="my-5">
      <Alert :title="action.title" v-if="action.title">
        {{ action.body }}
      </Alert>
    </div>
    <button v-if="isSupported" @click="askPermission"
      class="flex items-center ml-auto mr-auto bg-blue-500 hover:bg-blue-700 text-white text-sm font-bold py-2 px-4 rounded rounded-md">
      <Icon name="heroicons-outline:location-marker" size="1.5em" />
      Pedir permissão para notificações
    </button>
    <div v-else class="p-4 mb-4 text-sm text-red-800 rounded-lg bg-red-50 dark:bg-gray-800 dark:text-red-400"
      role="alert">
      <span class="font-medium">Notificações não é suportado no iPhone!</span> <br>
      Para isso, temos uma área de notificações internas do App e podemos avisar o cliente atráves de email e SMS
    </div>
  </section>
</template>
<script setup lang="ts">
import { useWebNotification } from '@vueuse/core'
import type { UseWebNotificationOptions } from '@vueuse/core'

const options: UseWebNotificationOptions = {
  title: 'Bem vindo ao seu App Web',
  body: 'Essa é uma mensagem automática que você poderá personalizar',
  dir: 'auto',
  lang: 'pt-br',
  renotify: true,
  tag: 'amb1io',
  icon: '/pwa/ios/100.png',
  requireInteraction: false
}

const {
  isSupported,
  show,
  onClick,
  onClose,
  onError
} = useWebNotification(options)

const action = ref({ title: '', body: '' })


onClick(e => {
  action.value = {
    title: "Você interagiu a notificação !",
    body: "Interagir com a notificação reflete com o site, aumentando a conversão e interação dos clientes"
  }
})

onClose(e => {
  action.value = {
    title: "Você fechou a notificação",
    body: "Interagir com a notificação reflete com o site, aumentando a conversão e interação dos clientes"
  }
})

function askPermission() {
  if (isSupported.value)
    show()
}
</script>