<script setup lang="ts">
import BaseButton from './BaseButton.vue'
import ArrowUp from './icons/ArrowUp.vue'

const emit = defineEmits<{
  (e: 'back-to-top'): void
}>()
</script>

<template>
  <footer class="footer">
    <BaseButton class="back-to-top" variant="ghost" type="button" aria-label="Back to top" @click="emit('back-to-top')">
      <ArrowUp />
    </BaseButton>
  </footer>
</template>

<style scoped>
.footer {
  margin-top: calc(var(--space) * 11.5);
  text-align: center;
  color: var(--muted);
  font-weight: 600;
  padding: 0 calc(var(--space) * 2) calc(var(--space) * 2.5);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: calc(var(--space) * 1.25);
}

.back-to-top {
  width: calc(var(--space) * 10);
  height: calc(var(--space) * 10);
  border-radius: 50%;
  border: 1px solid var(--line);
  background: var(--ink);
  color: var(--paper);
  font-weight: 700;
  font-size: 20px;
  cursor: pointer;
  transition: transform 160ms ease;
}

.back-to-top svg {
  min-width: calc(var(--space) * 7);
  fill: currentColor;
}

.back-to-top:hover {
  transform: scale(1.03);
}

.back-to-top:active {
  transform: scale(0.995);
}
</style>
