<script setup>
import { ref,onMounted } from 'vue';
import axios from 'axios'
import HeaderComponent from './components/HeaderComponent.vue'
import BlogGrid from './components/BlogGrid.vue';

let categories = ref([]);

getCategories();
async function getCategories() {
  let result = axios.get('https://basic-blog.teamrabbil.com/api/post-categories')
  result.then((response) => {
    if (response['data']) {
      categories.value = response['data'];
    }
  })
}
onMounted(() => {
  getCategories();
});
</script>
<template>
  <HeaderComponent :categories="categories" />
  <BlogGrid :categories="categories" />
</template>

<style scoped></style>
