<script setup>
import { shallowRef } from 'vue';
import TabTodos from './tabs/TabTodos.vue';
import TabElectronica from './tabs/TabElectronica.vue';
import TabPerifericos from './tabs/TabPerifericos.vue';
const tabActivoSin = shallowRef(TabTodos);
const tabActivoCon = shallowRef(TabTodos);


</script>

<template>
    <div class="contenedor">
        <h3>Parte 3</h3>
        <p>Mas dudas que respuestas :c</p>
    </div>
</template>

<style scoped>
.contenedor {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>