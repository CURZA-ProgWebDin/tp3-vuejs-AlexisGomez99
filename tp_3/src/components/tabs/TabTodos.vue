<script setup>
import { computed,onMounted,onUnmounted,onActivated,onDeactivated } from 'vue';
import { productos } from '../../data/productos';
import ListaPruductos from '../ListaPruductos.vue';

const prods = productos;
const productosFiltrados = computed(() => {
    return prods
})
onMounted(() => console.log('TabTodos — montado'))
onUnmounted(() => console.log('TabTodos — desmontado'))
onActivated(() => console.log('TabTodos — activado'))
onDeactivated(() => console.log('TabTodos — desactivado'))
</script>

<template>
    <ListaPruductos :productos="productosFiltrados" />
</template>