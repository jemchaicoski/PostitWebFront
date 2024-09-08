<template>
  <div class="layout">
    <AppSidebar />
    <router-view class="content" />
  </div>
</template>


<script setup>
import AppSidebar from './components/AppSidebar.vue';
</script>
