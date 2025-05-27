<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Актуальная дата: {{ currentDate }}</h2>
      <span>Открыто: <strong>{{ openRate }}</strong> | Прочитано: <strong>{{ readRate }}</strong></span>
    </div>
    <AppNews v-for="item in news" :title="item.title" :key="item.id" :id="item.id" :open="item.open"
      :was-read="item.wasRead" @open-news="openNews" @read-news="readNews" @unmark-news="unmarkNews" />
  </div>
</template>

<script setup>
import AppNews from "./AppNews.vue";
import { provide, ref } from "vue"

const news = [
  {
    id: 1,
    title: "First news about vue3",
    open: false,
    wasRead: false,
  },
  {
    id: 2,
    title: "Another one about the weather",
    open: false,
    wasRead: false,
  },
  {
    id: 3,
    title: "Same about vue3",
    open: false,
    wasRead: false,
  },
  {
    id: 4,
    title: "Miu",
    open: false,
    wasRead: false,
  },
];
const currentDate = new Date().toLocaleDateString();
const openRate = ref(0);
const readRate = ref(0);

const findNewsById = (id) => { return news.find(n => n.id === id) };

const openNews = () => {
  openRate.value++;
}

const readNews = (id) => {
  readRate.value++;
  const clickedNews = findNewsById(id);
  clickedNews.wasRead = true;
}

const unmarkNews = (id) => {
  readRate.value--;
  const clickedNews = findNewsById(id);
  clickedNews.wasRead = false;
}

provide('news-list', news);
provide('title', 'News list');
</script>

<style scoped>
h2 {
  color: red;
}
</style>
