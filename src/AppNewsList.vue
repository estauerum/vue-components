<template>
  <hr>
  <h4>{{ title }}</h4>
  <ul>
    <li v-for="item in newsList" :key="item">{{ item.title }} <span v-if="item.wasRead">!!!</span></li>
  </ul>
</template>

<script setup>
import { inject } from 'vue';

const newsList = inject('news-list', []);
const title = inject('title', '');

</script>
