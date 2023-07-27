<template>
  <main>
    <Header :installed=appIsInstalled />
    <VitePwaManifest />
    <NuxtLoadingIndicator />
    <NuxtPage />
    <appNav />
    <pwa-install manual-apple="true" manual-chrome="true" manifest-url="/manifest.webmanifest" />
  </main>
</template>
<style>
.page-enter-active,
.page-leave-active {
  position: fixed;
  transition: all 0.4s;
  width: inherit;
}

.page-enter-active {
  opacity: 1;
  transform: translateX(0)
}

.page-leave-from {
  opacity: 1;
  transform: translateX(0);
  z-index: -1;
}

.page-leave-active {
  opacity: 0;
  transform: translateX(-100%);
  z-index: -1;
  filter: blur(1rem);
}

.page-enter-from {
  opacity: 0;
  transform: translateX(100%);
  z-index: -1;
}
</style>
<script setup>
import '@khmyznikov/pwa-install';
import { onMounted } from 'vue'
import { initFlowbite } from 'flowbite'
let appIsInstalled = ref()
onMounted(() => {
  initFlowbite();
  if (document.getElementsByTagName("pwa-install").length > 0) {
    const pwaInstall = document.getElementsByTagName("pwa-install")[0]
    appIsInstalled.value = pwaInstall.isUnderStandaloneMode
  }
})
</script>
