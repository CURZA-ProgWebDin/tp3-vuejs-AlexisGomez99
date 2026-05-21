<script setup>
import { defineProps, onUnmounted, useTemplateRef, ref, onMounted, onUpdated, onBeforeUnmount } from 'vue';
import TarjetaProducto from './layouts/TarjetaProducto.vue';

const props = defineProps({ productos: { type: Array, required: true } });
const box = useTemplateRef('box');
const cargando = ref(true);
let timer = null;
function esperar(ms) {
    return new Promise(resolve => setTimeout(resolve, ms))
}
async function cargarProductos() {
    cargando.value = true;
    await esperar(800);
    console.log("Termino de cargar");
    cargando.value = false;
}
onMounted(async () => {
    await cargarProductos();

    timer = setInterval(() => {
        cargarProductos()
    }, 30000)
})

onUpdated(() => {
    if (box.value) {
        box.value.scrollTop = box.value.scrollHeight
    }
})

onBeforeUnmount(() => {
    clearInterval(timer)
    console.log('ListaProductos desmontado — polling detenido')
})
</script>

<template>
    <div class="listado_productos">
        <h3>Parte 2</h3>
        <div v-if="cargando">
            <h2>Cargando...</h2>
        </div>
        <div v-else ref="box" class="lista">
            <div v-for="prod in props.productos" key="prod.id">
                <TarjetaProducto>
                    <template #header> {{ prod.nombre }} - {{ prod.categoria }} </template>
                    <template #body="{ expandida, toggleExpandir }">
                        <div v-if="expandida === true">
                            <div>
                                <p>Stock : {{ prod.stock }}</p>
                                <p>Precio : ${{ prod.precio }}</p>
                            </div>

                        </div>
                        <a @click="toggleExpandir">{{ expandida ? 'cerrar' : 'ver mas' }}</a>
                    </template>
                    <template #footer><button @click="agregar_carrito">Comprar ahora</button></template>
                </TarjetaProducto>
            </div>
        </div>

    </div>
</template>

<style scoped>
.listado_productos {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.lista {
    max-height: 200px;
    overflow-y: auto;
}
</style>