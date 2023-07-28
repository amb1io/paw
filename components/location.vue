<template>
  <section>
    <header class="p-5">
      <h2 class="text-xl font-bold text-center">Peça a sua localização</h2>
      <p>É possível pedir sua localização. Se você aceitou quando a página abrir</p>
      <!-- <button @click="askLocation"
        class="flex items-center ml-auto mr-auto bg-blue-500 hover:bg-blue-700 text-white text-sm font-bold py-2 px-4 rounded rounded-md">
        <Icon name="heroicons-outline:location-marker" size="1.5em" />
        Pedir acesso a localização
      </button> -->
    </header>
    <div v-html="map"></div>
  </section>
</template>

<script setup>
import { useGeolocation } from '@vueuse/core'
const { coords } = useGeolocation()
const map = ref("")
watch(coords, value => {
  if (value.latitude != Infinity) {
    generateMap(value)
  }
})

function generateMap(coords) {
  const lat = coords.latitude
  const lng = coords.longitude
  const key = 'AIzaSyBY5PM-whNlVLfGJxfM_sCI_wUsFvl_Jzw'
  const url = `https://maps.googleapis.com/maps/api/geocode/json?latlng=${lat},${lng}&key=${key}`
  return fetch(url)
    .then(res => res.json())
    .then(res => {
      const address = res.results[0].formatted_address
      map.value = `<iframe class="w-full h-60" src="https://www.google.com/maps/embed/v1/place?key=${key}&q=${address}&zoom=18" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>`
    })
    .catch(err => console.log("err", err))
}
</script>