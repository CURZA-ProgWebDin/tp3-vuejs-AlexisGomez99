<script setup>
import { computed,onMounted,onUnmounted,onActivated,onDeactivated } from 'vue';
import { productos } from '../../data/productos';
import ListaPruductos from '../ListaPruductos.vue';

const prods = productos;
const productosFiltrados = computed(() => {
    return prods.filter(prod => prod.categoria === 'Periféricos');
})

onMounted(() => console.log('TabPerifericos — montado'))
onUnmounted(() => console.log('TabPerifericos — desmontado'))
onActivated(() => console.log('TabPerifericos — activado'))
onDeactivated(() => console.log('TabPerifericos — desactivado'))
</script>

<template>
    <ListaPruductos :productos="productosFiltrados" />
</template>