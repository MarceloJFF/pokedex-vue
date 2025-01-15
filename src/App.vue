<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>

    <div class="wrapper">

      <nav>
        <RouterLink to="/">Primeira geração</RouterLink>
        <RouterLink to="/geracao2">Segunda geração</RouterLink>
        <RouterLink to="/geracao3">Segunda geração</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>
