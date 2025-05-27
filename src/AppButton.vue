<template>
  <button class="btn" :class="props.color" @click="emit('action')">
    <slot />
  </button>
</template>

<script setup>
const props = defineProps({
  color: {
    type: String,
    default: '',
    validator(value) {
      return ['', 'primary', 'danger'].includes(value)
    }
  }
});

const emit = defineEmits({
  action: null,
})

const consoleBtn = () => {
  console.log('this is btn');
}

defineExpose({ consoleBtn });
</script>
