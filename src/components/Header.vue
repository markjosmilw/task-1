<script setup>
</script>

<template>
  <div class="main">
    <div class="header">
      <div id="nav">
        <router-link to="/">Home</router-link> |
        <router-link to="/contact">Contact Us</router-link> |
        <router-link to="/about">About Us</router-link>
      </div>
    </div>
    <div class="body">
      <router-view />
    </div>
  </div>
</template>