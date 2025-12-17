<script setup lang="ts">
import BaseButton from './BaseButton.vue'
import ArrowUp from './icons/ArrowUp.vue'

defineProps<{
  message: string
}>()

const emit = defineEmits<{
  (e: 'back-to-top'): void
}>()
</script>

<template>
  <footer class="footer">
    <p>{{ message }}</p>
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
  width: calc(var(--space) * 5.25);
  height: calc(var(--space) * 5.25);
  border-radius: 50%;
  border: 1px solid var(--line);
  background: var(--ink);
  color: var(--paper);
  font-weight: 700;
  font-size: 16px;
  cursor: pointer;
  box-shadow: 0 8px 18px rgba(0, 0, 0, 0.12);
  transition: transform 140ms ease, box-shadow 140ms ease;
}

.back-to-top svg {
  min-width: calc(var(--space) * 3.75);
  fill: currentColor;
}

.back-to-top:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.16);
}

.back-to-top:active {
  transform: translateY(0);
}
</style>
