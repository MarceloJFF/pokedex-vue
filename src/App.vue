<script setup>
import { RouterLink, RouterView } from 'vue-router'
import 'bootstrap/dist/css/bootstrap.min.css'
import './complementos/estilos.css'
import BarraDeNavagecao from './componentes/BarraDeNavagecao.vue';
</script>

<template>
  <BarraDeNavagecao></BarraDeNavagecao>
  
  <RouterView />
</template>
