<script setup lang="ts">
interface Article {
  createdAt: string,
  description: string,
  id: number | string,
  image: string,
  preview: string,
  title: string,
}

const article = ref<Article>();
const route = useRoute()
onMounted(async () => {
  try {
    const response = await fetch(`https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${route.params.id}`);
    article.value = await response.json();
  } catch (error) {
    console.error("Ошибка загрузки статей:", error);
  }
});
</script>

<template>
  <div class="articles">
    <div class="container">
      <h2 class="articles__title">{{ article?.title }}</h2>
      <div class="articles__img">
        <img src="/assets/images/holder.png" alt="">
      </div>
      <span>About</span>
      <p class="articles__description">
        {{ article?.description }}
      </p>
    </div>
  </div>
</template>

<style scoped>

</style>