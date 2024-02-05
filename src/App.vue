<script setup>
import { ref } from 'vue'

const titulo = ref('Lista de la compra')
const productos = ref([])
const productoNuevo = ref('')
const esImportante = ref(false)

const añadirALaLista = () => {
  productos.value.push({
    id: productos.value.length + 1,
    nombre: productoNuevo.value
  })
  productoNuevo.value = ''
}
</script>

<template>
  <h1>{{ titulo }}</h1>
  <form class="add-item-form" @submit.prevent="añadirALaLista()">
    <input
      v-model="productoNuevo"
      type="text"
      placeholder="Que quieres comprar?"
    />
    <label>
      <input v-model="esImportante" type="checkbox" />
      Muy importante
    </label>
    <button class="btn btn-primary">Añadir producto</button>
  </form>
  <ul>
    <li v-for="{ id, nombre } in productos" :key="id">
      {{ nombre }} - {{ id }}
    </li>
  </ul>

  <p v-if="!productos.length">La lista está vacia</p>
</template>
