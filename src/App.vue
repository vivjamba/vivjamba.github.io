<script setup>
import FooterSection from './components/FooterSection.vue'
</script>

<template>
  <router-view />
  <FooterSection />
</template>

<style>
html, body, #app {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
}

main {
  margin: 0;
  padding: 0;
}
</style>
