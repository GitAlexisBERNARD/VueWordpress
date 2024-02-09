<script setup lang="ts">
import { ref, onMounted } from 'vue';

const listeArticles = ref([]);

onMounted(() => {
  fetch("http://localhost/VueWordpress/wp-json/wp/v2/posts")
    .then(response => response.json())
    .then(data => {
      listeArticles.value = data;
    })
    .catch(error => console.error("Erreur lors de la récupération des articles:", error));
});
</script>
<template>
    <h1 class="p-5 font-bold">Liste des Articles WordPress</h1>
    <ul>
    <li v-for="article in listeArticles" :key="article.id">
      <h2>{{ article.title.rendered }}</h2>
      <div v-html="article.content.rendered"></div>
      <img v-if="article._embedded && article._embedded['wp:featuredmedia']" :src="article._embedded['wp:featuredmedia'][0].source_url" alt="Image de l'article">
    </li>
  </ul>
</template>

<style scoped>
  img {
    width: 100px !important;
  }
</style>