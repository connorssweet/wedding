<script setup lang="ts">
const props = defineProps<{
  variant?: 'primary' | 'ghost'
  type?: 'button' | 'submit' | 'reset'
}>()

const variantClass = props.variant ? `button--${props.variant}` : 'button--ghost'
</script>

<template>
  <button :type="props.type ?? 'button'" class="button" :class="variantClass">
    <slot />
  </button>
</template>
