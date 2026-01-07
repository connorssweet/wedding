<script setup lang="ts">
import BaseButton from './BaseButton.vue'

defineProps<{
  rsvpLink: string
}>()
</script>

<template>
  <section class="section rsvp" id="rsvp">
    <div class="rsvp-card">
      <div>
        <p class="muted">
          Please let us know if you can join. We cannot wait to celebrate together.
        </p>
      </div>
      <BaseButton variant="primary" type="button">
        <a :href="rsvpLink" target="_blank" rel="noreferrer">RSVP</a>
      </BaseButton>
    </div>
  </section>
</template>

<style scoped>
.rsvp-card {
  margin-top: calc(var(--space) * 3.5);
  display: flex;
  gap: calc(var(--space) * 2.25);
  align-items: center;
  justify-content: space-between;
  padding: calc(var(--space) * 2.75) calc(var(--space) * 3);
  border-radius: calc(var(--space) * 2.25);
  background: var(--paper);
  border: 1px solid var(--line);
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.06);
}

@media (max-width: 640px) {
  .rsvp-card {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
