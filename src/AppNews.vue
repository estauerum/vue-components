<template>
  <div class="card">
    <h3>({{ id }}) {{ title }}</h3>
    <AppButton @action="toggleOpen"> {{ setButtonValue() }} </AppButton>
    <AppButton v-if="wasRead" @action="emit('unmark-news', id)" color="danger">Mark as unread</AppButton>
    <div v-if="localOpen">
      <p>This is the news p about what happened</p>
      <AppButton v-if="!wasRead" @action="markNews(id)" class="primary">Read news</AppButton>
      <AppNewsList></AppNewsList>
    </div>
  </div>
</template>

<script setup>
import { toRef } from "vue";
import AppButton from "./AppButton.vue";
import AppNewsList from "./AppNewsList.vue";

const props = defineProps({
  title: {
    type: String,
    required: true,
    default: "Тайтл",
  },
  id: {
    type: Number,
    required: true
  },
  open: {
    type: Boolean,
    required: false,
    default: false,
  },
  wasRead: {
    type: Boolean,
    required: true
  }
});
const emit = defineEmits({
  'open-news': null,
  'read-news'(id) {
    if (id) return true
    else console.warn('no id for emit read-news');
  },
  'unmark-news'(id) {
    if (id) return true
    else console.warn('no id for emit read-news');
  },
});

const localOpen = toRef(props.open);

const toggleOpen = () => {
  localOpen.value = !localOpen.value;
  if (localOpen.value) emit('open-news', 42);
};

const markNews = (id) => {
  emit('read-news', id);
  localOpen.value = false;
}

const setButtonValue = () => {
  return localOpen.value ? 'close' : 'open';
}

const wasRead = toRef(props, 'wasRead');
</script>
