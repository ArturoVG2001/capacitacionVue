<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <nav class="navbar bg-dark navbar-dark">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">
        <img src="@/assets/logo.svg" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
        PokeAPI
      </router-link>
      <div>
        <router-link class="btn btn-outline-primary me-2" to="/" active-class="active">Home</router-link>
        <router-link class="btn btn-outline-primary me-2" to="/pokemons" active-class="active">Pokemons</router-link>
        <router-link class="btn btn-outline-primary " to="/favoritos" active-class="active">Favoritos</router-link>
      </div>
    </div>
  </nav>
  <div class="container text-center">
    <RouterView />

  </div>
</template>

<style scoped></style>