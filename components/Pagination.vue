<script setup lang="ts">
import { computed } from "vue";

interface Props {
  totalItems: number;
  itemsPerPage?: number;
  currentPage: number;
}

const props = defineProps<Props>();
const emit = defineEmits(["update:currentPage"]);

const totalPages = computed(() => Math.ceil(props.totalItems / (props.itemsPerPage || 10)));

const changePage = (page: number) => {
  if (page >= 1 && page <= totalPages.value) {
    emit("update:currentPage", page);
  }
};
</script>

<template>
  <div class="pagination">
    <button
        @click="changePage(currentPage - 1)"
        v-if="currentPage !== 1"
        class="pagination__item pagination__prev"
    ><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M9.5 7.5L14.5 12.5L9.5 17.5" stroke="#494949" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>

    </button>

    <button
        v-for="page in totalPages"
        :key="page"
        @click="changePage(page)"
        :class="[
        'pagination__item pagination__page',
        { 'pagination__current': page === currentPage, 'pagination__disabled': page !== currentPage }
      ]"
    >
      {{ page }}
    </button>

    <button
        @click="changePage(currentPage + 1)"
        v-if="currentPage !== totalPages"
        class="pagination__item pagination__next"
    ><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M9.5 7.5L14.5 12.5L9.5 17.5" stroke="#494949" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
    </button>
  </div>
</template>
