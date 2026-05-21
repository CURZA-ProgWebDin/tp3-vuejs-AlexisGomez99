<script setup>
import { computed,onMounted,onUnmounted,onActivated,onDeactivated } from 'vue';
import { productos } from '../../data/productos';
import ListaPruductos from '../ListaPruductos.vue';

const prods = productos;
const productosFiltrados = computed(() => {
    return prods.filter(prod => prod.categoria === 'Electrónica');
})

onMounted(() => console.log('TabElectronica — montado'))
onUnmounted(() => console.log('TabElectronica — desmontado'))
onActivated(() => console.log('TabElectronica — activado'))
onDeactivated(() => console.log('TabElectronica — desactivado'))
</script>

<template>
    <ListaPruductos :productos="productosFiltrados" />
</template>