<template>
  <div class="container pt-1">
    <div class="card">
      <AppAsyncComp />
      <h2>Dinamic and Async components</h2>
      <AppButton ref="myBtn" @action="active = 'one'" :color="oneColor">One</AppButton>
      <AppButton @action="active = 'two'" :color="twoColor">TWo</AppButton>
    </div>
    <KeepAlive>
      <component :is="componentName"></component>
    </KeepAlive>
  </div>
</template>

<script setup>
import AppButton from './AppButton.vue';
import AppTextOne from './AppTextOne.vue';
import AppTextTwo from './AppTextTwo.vue';
import { computed, onMounted, ref, defineAsyncComponent } from 'vue';

const myBtn = ref(null);
const active = ref('one')

const AppAsyncComp = defineAsyncComponent(() => import('./AppAsyncComp.vue'));

const componentName = computed(() => {
  return active.value === 'one' ? AppTextOne : AppTextTwo;
})

const oneColor = computed(() => {
  return active.value === 'one' ? 'primary' : '';
});
const twoColor = computed(() => {
  return active.value === 'two' ? 'primary' : '';
});

onMounted(() => {
  myBtn.value.consoleBtn();
})
</script>

<style></style>
