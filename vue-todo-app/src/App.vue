<template>
  <div class="page">
    <AppHeader/>
    <main>
      <Todos/>
    </main>
    <AppFooter/>
  </div>
</template>

<script setup>
import AppHeader from "@/components/AppHeader.vue";
import AppFooter from "@/components/AppFooter.vue";
import Todos from "@/components/Todos.vue";
</script>
