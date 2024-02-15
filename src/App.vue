<script setup>
import { ref } from 'vue'
import ListaProductos from './componentes/ListaProductos.vue'

const titulo = ref('Lista de la compra')
const productoNuevo = ref('')
const esImportante = ref(false)

const productos = ref([])

const añadirALaLista = () => {
  productos.value.push({
    id: productos.value.length + 1,
    nombre: productoNuevo.value,
    importante: esImportante.value
  })
  productoNuevo.value = ''
  esImportante.value = false
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
  <ListaProductos :productos="productos" />

  <p v-if="!productos.length">La lista está vacia</p>
</template>
