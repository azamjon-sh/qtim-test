<script setup lang="ts">
interface Article {
  createdAt: string;
  description: string;
  id: number | string;
  image: string;
  preview: string;
  title: string;
}

defineProps<{ article: Article }>();
</script>

<template>
  <NuxtLink :to="`/article/${article.id}`" class="card">
    <div class="card__img">
      <img src="/assets/images/holder.png" alt="">
    </div>
    <h3 class="card__title">
      {{ article.title }}
    </h3>
    <div class="card__link">Read more</div>
  </NuxtLink>
</template>

<style scoped>

</style>