<script setup lang="ts">

interface Article {
  createdAt: string,
  description: string,
  id: number | string,
  image: string,
  preview: string,
  title: string,
}


const totalItems = ref<number>(0)
const itemsPerPage = ref<number>(8)
const currentPage = ref<number>(2)

const articles = ref<Article[]>([]);
onMounted(async () => {
  try {
    const response = await fetch('https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts');
    articles.value = await response.json();
    totalItems.value = articles.value.length
  } catch (error) {
    console.error("Ошибка загрузки статей:", error);
  }
});

  const sortedArticles = computed(() => {
    const start = (currentPage.value - 1) * itemsPerPage.value;
    const end = start + itemsPerPage.value;
    return articles.value.slice(start, end);
  });

</script>

<template>
  <div class="articles">
    <div class="container">
      <h2 class="articles__title">Articles</h2>

      <div class="articles__grid" v-if="sortedArticles.length">
        <template v-for="article in sortedArticles" :key="article.id">
          <Card :article="article"/>
        </template>
      </div>
      <Pagination v-model:currentPage="currentPage"
                  :items-per-page="itemsPerPage"
                  :total-items="totalItems"/>
    </div>
  </div>
</template>

<style scoped>

</style>