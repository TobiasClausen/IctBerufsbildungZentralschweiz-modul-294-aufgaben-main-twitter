<script setup>
import IconLogin from './icons/IconLogin.vue'
import IconHome from './icons/IconHome.vue'
</script>

<template>
  <nav class="nav">
    <RouterLink to="/">
      <IconHome />
      Stream
    </RouterLink>
    <RouterLink to="/login">
      <IconLogin />
      Login
    </RouterLink>
  </nav>
</template>

<style scoped>
.nav {
  display: flex;
  flex-direction: column;
}

.nav a {
  font-size: 1.2rem;
  display: flex;
  align-items: center;
  padding: 12px 0;
  color: #64748b;
}

.nav a.router-link-active,
.nav a:hover {
  color: inherit;
}

.nav a svg {
  width: 30px;
  margin-right: 30px;
}
</style>