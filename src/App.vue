<script setup>
import BlogPost from './components/BlogPost.vue';
import { ref, onMounted } from "vue";
import PagintePost from './components/PaginatePost.vue';
import LoadingSpinner from './components/LoadingSpinner.vue'
const posts = ref([]);
const inicio = ref(0);
const fin = ref(postXpage);
const postXpage = 10;
const loading = ref(true);

const favorito = ref('');

const cambiarFavorito = (title) => {
  favorito.value = title;
};



const next = () => {
  inicio.value += postXpage;
  fin.value += postXpage;
}

const prev = () => {
  inicio.value = inicio.value - postXpage;
  fin.value = fin.value - postXpage;
}

const fetchData = async () => {
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts');
    posts.value = await res.json();

  } catch (error) {
    console.log(error);
  } finally {
    loading.value = false;
  }
}

fetchData();
</script>

<template>
  <LoadingSpinner v-if="loading"></LoadingSpinner>
  <div class="container" v-else>
    <h1>APP</h1>
    <h2>Mi post favorito: {{ favorito }}</h2>

    <PagintePost class="mb-2" :next="next" :prev="prev" :inicio="inicio" :fin="fin" :count="posts.length"></PagintePost>
    <BlogPost v-for="post in posts.slice(inicio, fin)" :key="post.id" :title="post.title" :id="post.id" :body="post.body"
      :cambiarFavorito="cambiarFavorito" />
  </div>
</template>
