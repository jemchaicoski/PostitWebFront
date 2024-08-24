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

<style Lang="sass" scoped>
.layout {
  display: contents;
  min-height: 100vh;
  min-width: 100vh;
}

.content {
  display: flex;
  justify-content: center;
  margin: 0;
  width: 100%;
  height: 100%;
  padding: 2rem;
}
</style>
