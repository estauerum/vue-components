<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Slots</h2>
    </div>
    <AppList>
      <template #default="{ iter, idx }">
        <span style="color: #ccc">item:{{ iter }} idx:{{ idx }}</span>
      </template>

    </AppList>
    <AppBlock>
      <h3>This is title</h3>
      <p>Это самый важный текст.</p>
      <template #footer>
        <hr>
        <small>This is footer</small>
      </template>
    </AppBlock>
  </div>
</template>

<script setup>
import AppBlock from './AppBlock.vue';
import AppList from './AppList.vue';
</script>

<style></style>
