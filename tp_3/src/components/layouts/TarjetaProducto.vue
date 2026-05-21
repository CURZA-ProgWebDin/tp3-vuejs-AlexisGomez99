<script setup>
import { ref, defineProps } from 'vue';

const expandida = ref(false);
const toggleExpandir = () => {
    expandida.value = !expandida.value;
}
</script>

<template>
    <div class="contenedor_tarjeta">
        <header>
            <slot name="header"></slot>
        </header>

        <body>
            <slot name="body" :expandida="expandida" :toggleExpandir="toggleExpandir"></slot>
        </body>
        <footer>
            <slot name="footer">
                <span>Sin acciones disponibles</span>
            </slot>
        </footer>
    </div>
</template>
<style scoped>
.contenedor_tarjeta {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    align-items: center;
    border: solid 1px;
    width: 300px;
    height: auto;
}
</style>