<template>
  <AppSidebar />
  <div class="content">
    <router-view />
  </div>

</template>

<script setup>
import AppSidebar from './components/AppSidebar.vue';
</script>

<style>
  .content {
    display: flex;
    align-content: center;

    @media (min-width: 1024px) {
      * {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 2%;
      }
    } 
  }
</style>