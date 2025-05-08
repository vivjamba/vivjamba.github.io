<template>
  <div class="nav-text-links" :class="{ textLight }">
    <router-link
      to="/"
      :class="{ active: route.path === '/' }"
      aria-label="Home"
    >Home</router-link>

    <router-link
      :to="{ path: '/', hash: '#experience-section' }"
      aria-label="Experience"
    >Experience</router-link>

    <router-link
      to="/about"
      :class="{ active: route.path === '/about' }"
      aria-label="About Me"
    >About Me</router-link>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router'

defineProps({
  textLight: {
    type: Boolean,
    default: false
  }
})

const route = useRoute()
</script>

<style scoped>
.nav-text-links {
  position: absolute;
  top: 1.5rem;
  left: 2rem;
  z-index: 10;
  display: flex;
  gap: 1.8rem;

  --link-color: black;
  --hover-bg: rgba(0, 0, 0, 0.1);
}

.nav-text-links.textLight {
  --link-color: white;
  --hover-bg: rgba(255, 255, 255, 0.15);
}

.nav-text-links a {
  color: var(--link-color);
  font-size: 1.4rem;
  font-weight: 500;
  padding: 0.4rem 0.8rem;
  border-radius: 6px;
  transition: background-color 0.3s ease, opacity 0.3s ease;
  text-decoration: none;
  cursor: pointer;
}

.nav-text-links a:hover {
  background-color: var(--hover-bg);
  opacity: 0.85;
}

.nav-text-links a.active {
  text-decoration: underline;
}
</style>
