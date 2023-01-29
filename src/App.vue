<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="container d-flex align-items-center justify-content-center fs-2">
    <p>FELLOWSHIP BIBLE CHURCH</p>
  </div> 
  <header>
    <div class="container d-flex align-items-center justify-content-center fs-6">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/missions">Missions</RouterLink>
        <RouterLink to="/beliefs">Beliefs</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>
        <a href="https://live.fbcmn.org/">Sermons</a>
      </nav>
    </div>
  </header>

  <div class="container-xxl">
      <hr class="text-secondary mt-0">
    </div>
  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.0;
  max-height: 100vh;
}

nav {
  width: 90%;
  font-size: 14px;
  text-align: center;  
  margin-bottom: 14px;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
  }

  nav {
    text-align: center;
    font-size: 1rem;
    margin-top: 1rem;
  }
}
</style>
