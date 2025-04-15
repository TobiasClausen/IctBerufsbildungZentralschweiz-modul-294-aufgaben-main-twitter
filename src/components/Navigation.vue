<script setup>
import IconLogin from './icons/IconLogin.vue'
import IconHome from './icons/IconHome.vue'
</script>

<template>
  <nav class="nav">
    <a href="#" class="router-link-active">
      <IconHome />
      Stream
    </a>
    <a href="#">
      <IconLogin />
      Login
    </a>
  </nav>
</template>