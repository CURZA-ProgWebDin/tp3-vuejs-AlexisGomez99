<script setup>
import ListaPruductos from './components/ListaPruductos.vue';
import PanelPestanas from './components/PanelPestanas.vue';
import Home from './components/views/Home.vue';
import { productos } from './data/productos';

const prods = productos;
</script>

<template>
  <Home :prods="prods" />
  <ListaPruductos :productos="prods" />
  <PanelPestanas />
</template>
