<script setup>
import { KeepAlive, ref } from 'vue';
import TabTodos from './tabs/TabTodos.vue';
import TabElectronica from './tabs/TabElectronica.vue';
import TabPerifericos from './tabs/TabPerifericos.vue';

const components = {
    TabTodos,
    TabElectronica,
    TabPerifericos
};

const currentConKeep = ref("TabTodos");
const currentSinKeep = ref("TabTodos");


/**
 * Conviene usar keepAlive para cuando ya tenes los datos no necesitas hacer otra consulta a la base de datos 
 * En cambio, si no se utiliza el keepAlive vuelve a cargar el componente haciendo que se ejecute el onMounted y posiblemente ahi se encuentre la peticion para la base
 * Si nada cambio o se actualizo conviene usar el keepAlive pero si puede cambiar constantementes cuando se recargan los componentes conviene no usarlo para tener
 * la informacion de la bd mas reciente
 */
</script>

<template>
    <div class="contenedor">
        <h4>Sin KeepAlive</h4>
        <div class="Interfaz-sin-keep">
            <ul>
                <li v-for="(_, index) in components" key="index">
                    <button @click=" currentSinKeep = index">{{ index }}</button>
                </li>
            </ul>
            <component :is="components[currentSinKeep]" />
        </div>
        <h4>Con KeepAlive</h4>
        <div class="Interfaz-con-keep">
            <ul>
                <li v-for="(_, index) in components" key="index">
                    <button @click=" currentConKeep = index">{{ index }}</button>
                </li>
            </ul>
            <KeepAlive>
                <component :is="components[currentConKeep]" />
            </KeepAlive>
        </div>
    </div>
</template>

<style scoped>
.contenedor {
    border: solid 1px;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>