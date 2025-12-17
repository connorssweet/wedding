<script setup lang="ts">
import BaseButton from './BaseButton.vue'

const props = defineProps<{
  title: string
  subtitle: string
  dateMain: string
  dateSmall: string
}>()

const emit = defineEmits<{
  (e: 'scroll-rsvp'): void
  (e: 'scroll-schedule'): void
}>()
</script>

<template>
  <header class="hero">
    <div class="hero-content">
      <h1>{{ props.title }}</h1>
      <p class="lede">{{ props.subtitle }}</p>
      <div class="hero-date">
        <span class="date-main">{{ props.dateMain }}</span>
        <span class="date-small">{{ props.dateSmall }}</span>
      </div>
      <div class="hero-actions">
        <BaseButton variant="primary" @click="emit('scroll-rsvp')">RSVP</BaseButton>
        <BaseButton variant="ghost" @click="emit('scroll-schedule')">View schedule</BaseButton>
      </div>
    </div>
  </header>
</template>

<style scoped>
.hero {
  position: relative;
  overflow: hidden;
  border-radius: 34px;
  background-color: var(--paper);
  padding: clamp(calc(var(--space) * 6), 6vw, calc(var(--space) * 10.75))
    clamp(calc(var(--space) * 3.5), 6vw, calc(var(--space) * 10.25));
  display: grid;
  grid-template-columns: minmax(0, 7fr) minmax(240px, 3fr);
  gap: clamp(calc(var(--space) * 2.25), 3vw, calc(var(--space) * 4));
  min-height: 78vh;
  border: 1px solid var(--line);
  box-shadow: 0 18px 42px rgba(0, 0, 0, 0.05);
  isolation: isolate;
}

.hero::before {
  content: '';
  position: absolute;
  inset: 0;
  background: url('photos/hero-bg.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  transform: rotate(180deg);
  transform-origin: center;
  z-index: -1;
}

.hero-content {
  position: relative;
  z-index: 1;
  align-self: center;
  max-width: 640px;
}

.hero h1 {
  font-size: clamp(52px, 8vw, 96px);
  margin: 0;
  line-height: 0.96;
  color: var(--ink);
  font-weight: 600;
}

.hero h1 span {
  font-weight: 600;
}

.lede {
  font-size: 20px;
  margin: calc(var(--space) * 2.25) 0 calc(var(--space) * 3);
  color: var(--muted);
  text-transform: lowercase;
  letter-spacing: 0.02em;
}

.hero-date {
  display: flex;
  align-items: center;
  gap: calc(var(--space) * 1.75);
  padding: calc(var(--space) * 1.75) calc(var(--space) * 2);
  border-radius: calc(var(--space) * 2);
  background: rgba(255, 255, 255, 0.9);
  border: 1px solid var(--line);
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.04);
  width: fit-content;
}

.date-main {
  font-weight: 700;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.date-small {
  font-size: 14px;
  color: var(--muted);
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: calc(var(--space) * 1.5);
  margin-top: calc(var(--space) * 3.5);
}

@media (max-width: 980px) {
  .hero {
    grid-template-columns: 1fr;
    min-height: 70vh;
  }
}

@media (max-width: 640px) {
  .hero {
    padding: 38px 24px;
  }

  .hero-actions {
    width: 100%;
  }
}
</style>
