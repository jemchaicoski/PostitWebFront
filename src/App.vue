<template>
  <div class="app">
    <AppSidebar />
    <router-view />
  </div>

</template>

<script setup>
import AppSidebar from './components/AppSidebar.vue';
</script>