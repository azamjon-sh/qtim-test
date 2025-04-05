<script setup lang="ts">

import AppButton from "~/components/AppButton.vue";
</script>

<template>
  <header class="header">
    <div class="header__logo">
      <NuxtLink to="/"><img src="/assets/images/logo.svg" alt=""></NuxtLink>
    </div>
    <div class="header__actions">
      <NuxtLink to="/" class="header__link">Works</NuxtLink>
      <NuxtLink to="/" class="header__link">About</NuxtLink>


      <div class="header__lang">
        <img src="/assets/images/eng.svg" alt="">
      </div>
      <AppButton class="header__btn">Let’s work</AppButton>
    </div>
  </header>
</template>

<style scoped>

</style>