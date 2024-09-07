<template>
  <div class="layout">
    <AppSidebar />
    <div class="content">
      <router-view />
    </div>
  </div>
</template>


<script setup>
import AppSidebar from './components/AppSidebar.vue';
</script>
