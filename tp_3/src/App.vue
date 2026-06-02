<script setup>
import ListaPruductos from './components/ListaPruductos.vue';
import PanelPestanas from './components/PanelPestanas.vue';
import Home from './components/views/Home.vue';
import { productos } from './data/productos';

const prods = productos;
</script>

<template>
  <h3>Parte 1</h3>
  <Home :prods="prods" />
  <h3>Parte 2</h3>
  <ListaPruductos :productos="prods" />
  <h3>Parte 3</h3>
  <PanelPestanas />
</template>
