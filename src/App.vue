<script setup>
import { ref, onMounted } from 'vue'
import { db } from './data/guitarras'
import Guitarra from './components/Guitarra.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

//Para valores como bolean, string, etc.
const guitarras = ref([])
const carrito = ref([])

onMounted(() => {
  guitarras.value = db
})

const agregarCarrito = (guitarra) => {
  guitarra.cantidad = 1
  carrito.value.push(guitarra)
}
</script>

<template>
  <Header />
  <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Colección</h2>

    <div class="row mt-5">
      <Guitarra
        @agregar-carrito="agregarCarrito"
        v-for="guitarra in guitarras"
        v-bind:guitarra="guitarra"
        v-bind:key="guitarra.id"
      />
    </div>
  </main>

  <Footer />
</template>
