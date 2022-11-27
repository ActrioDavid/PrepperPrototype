<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid">
        <RouterLink class="navbar-brand mb-0 h1" to="/">Home</RouterLink>
      </div>
    </nav>
  </header>
<div>
  <center><RouterView /></center>
</div>
</template>

<style scoped>
</style>
