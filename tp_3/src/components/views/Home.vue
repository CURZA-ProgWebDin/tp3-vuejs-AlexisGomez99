<script setup>
import TarjetaProducto from '../layouts/TarjetaProducto.vue';
const props = defineProps(['prods']);

const agregar_carrito = () => {
    alert('Se agrego al carrito.')
}
</script>
<template>
    <div class="listado_productos" v-if="props.prods && props.prods.length > 0">
        <h1>PRODUCTOS</h1>
        <TarjetaProducto>
            <template #header> {{ props.prods[0].nombre }} - {{ props.prods[0].categoria }} </template>
            <template #body="{ expandida, toggleExpandir }">
                <div v-if="expandida === true">
                    <div>
                        <p>Stock : {{ props.prods[0].stock }}</p>
                        <p>Precio : ${{ props.prods[0].precio }}</p>
                    </div>

                </div>
                <a @click="toggleExpandir">{{ expandida ? 'cerrar' : 'ver mas' }}</a>
            </template>
            <template #footer>
                <button @click="agregar_carrito">Comprar ahora</button>
            </template>
        </TarjetaProducto>
        <TarjetaProducto>
            <template #header> {{ props.prods[1].nombre }} - {{ props.prods[1].categoria }} </template>
            <template #body="{ expandida, toggleExpandir }">
                <div v-if="expandida === true">
                    <div>
                        <p>Stock : {{ props.prods[1].stock }}</p>
                        <p>Precio : ${{ props.prods[1].precio }}</p>
                    </div>

                </div>
                <a @click="toggleExpandir">{{ expandida ? 'cerrar' : 'ver mas' }}</a>
            </template>
        </TarjetaProducto>
        <TarjetaProducto>
            <template #header> {{ props.prods[2].nombre }} - {{ props.prods[2].categoria }} </template>
            <template #body="{ expandida, toggleExpandir }">
                <div v-if="expandida === true">
                    <div>
                        <p>Stock : {{ props.prods[2].stock }}</p>
                        <p>Precio : ${{ props.prods[2].precio }}</p>
                    </div>

                </div>
                <a @click="toggleExpandir">{{ expandida ? 'cerrar' : 'ver mas' }}</a>
            </template>
            <template #footer>
                <button @click="agregar_carrito">Comprar ahora</button>
            </template>
        </TarjetaProducto>
    </div>
</template>

<style scoped>
.listado_productos {
    border: solid 1px;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>