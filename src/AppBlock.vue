<template>
  <div class="card">
    <slot> No text </slot>
    <div v-if="slots.footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script setup>
import { useSlots } from 'vue';

const slots = useSlots();
</script>

<style></style>
