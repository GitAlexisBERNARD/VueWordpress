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
  <div>
    <h1>WordPress Headless</h1>
    <section>
      <h2>Liste des Articles</h2>
      <ul>
        <li v-for="article in listeArticles" :key="article.id">
          {{ article.title.rendered }}
        </li>
      </ul>
      <img src="http://localhost/VueWordpress/wp-content/uploads/2024/01/pp.png" alt="Image par défaut">
    </section>
  </div>
</template>
