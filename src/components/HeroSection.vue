<script setup lang="ts">
import BaseButton from './BaseButton.vue'

const props = defineProps<{
  title: string
  subtitle: string
  dateMain: string
  dateSmall: string
  rsvpLink: string
}>()

const emit = defineEmits<{
  (e: 'scroll-schedule'): void
}>()

const openRsvp = () => {
  if (props.rsvpLink) {
    window.open(props.rsvpLink, '_blank', 'noreferrer')
  }
}
</script>

<template>
  <header class="hero">
    <div class="hero-garland garland-tl"></div>
    <div class="hero-garland garland-tr"></div>
    <div class="hero-garland garland-bl"></div>
    <div class="hero-garland garland-br"></div>
    <div class="hero-content">
      <div class="hero-divider"></div>
      <p class="hero-subtitle">{{ props.subtitle }}</p>
      <h1 class="hero-title">{{ props.title }}</h1>

      <div class="hero-meta">
        <div class="hero-date">
          <span class="date-main">{{ props.dateMain }}</span>
          <span class="date-small">{{ props.dateSmall }}</span>
        </div>
        <div class="hero-actions">
          <BaseButton variant="primary" @click="openRsvp">RSVP</BaseButton>
          <BaseButton variant="ghost" @click="emit('scroll-schedule')">View schedule</BaseButton>
        </div>
      </div>

      <div class="hero-divider rotated"></div>
    </div>
  </header>
</template>

<style scoped>
.hero {
  position: relative;
  overflow: visible;
  border-radius: 0;
  background-color: var(--paper);
  padding: clamp(calc(var(--space) * 6), 6vw, calc(var(--space) * 10.75))
    clamp(calc(var(--space) * 3.5), 6vw, calc(var(--space) * 10.25));
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  min-height: 78vh;
  border: none;
  box-shadow: none;
  isolation: isolate;
  width: 100vw;
  margin-left: calc((100vw - 100%) / -2);
  margin-top: 0;
}

.hero-content {
  position: relative;
  z-index: 1;
  align-self: center;
  max-width: 1100px;
  display: grid;
  gap: clamp(calc(var(--space) * 5), 8vw, calc(var(--space) * 10));
}

.hero-title {
  font-family: 'Amoresa Aged', 'Playfair Display', 'Times New Roman', serif;
  font-size: clamp(74px, 14vw, 140px);
  margin: 0;
  line-height: 1.05;
  color: var(--ink);
  font-weight: 600;
  animation-delay: 120ms;
}

.hero-subtitle {
  font-family: 'London', 'Times New Roman', serif;
  font-size: clamp(20px, 3vw, 28px);
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--ink);
  margin: 0;
  margin-bottom: clamp(calc(var(--space) * 4), 6vw, calc(var(--space) * 7));
  animation-delay: 60ms;
}

.hero-date {
  display: flex;
  align-items: center;
  gap: calc(var(--space) * 1.75);
  padding: calc(var(--space) * 1.75) calc(var(--space) * 2.25);
  border-radius: calc(var(--space) * 2);
  background: rgba(255, 255, 255, 0.9);
  border: 1px solid var(--line);
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.04);
  width: fit-content;
  margin: 0 auto;
}

.date-main {
  font-weight: 700;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.date-small {
  font-size: 20px;
  color: var(--muted);
}

.hero-meta {
  display: grid;
  gap: calc(var(--space) * 2.5);
  justify-items: center;
  margin-top: calc(var(--space) * 2);
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: calc(var(--space) * 1.5);
  justify-content: center;
  animation-delay: 180ms;
}

.hero-divider {
  width: min(520px, 94%);
  margin: 0 auto;
  height: 34px;
  background-color: var(--ink);
  mask-image: url('divider.svg');
  -webkit-mask-image: url('divider.svg');
  mask-repeat: no-repeat;
  -webkit-mask-repeat: no-repeat;
  mask-position: center;
  -webkit-mask-position: center;
  mask-size: contain;
  -webkit-mask-size: contain;
}

.hero-divider.rotated {
  transform: rotate(180deg);
}

.hero-garland {
  position: absolute;
  width: clamp(220px, 22vw, 280px);
  height: auto;
  pointer-events: none;
  opacity: 0.9;
  aspect-ratio: 6 / 7;
  background-color: var(--ink);
  mask-image: url('garland.svg');
  -webkit-mask-image: url('garland.svg');
  mask-repeat: no-repeat;
  -webkit-mask-repeat: no-repeat;
  mask-size: contain;
  -webkit-mask-size: contain;
  mask-position: center;
  -webkit-mask-position: center;
}

.garland-tl {
  top: 12px;
  left: 12px;
}

.garland-tr {
  top: 12px;
  right: 12px;
  transform: scaleX(-1);
}

.garland-bl {
  bottom: 12px;
  left: 12px;
  transform: scaleY(-1);
}

.garland-br {
  bottom: 12px;
  right: 12px;
  transform: scale(-1, -1);
}

@media (max-width: 900px) {
  .hero-garland {
    width: clamp(140px, 20vw, 200px);
  }
}

@media (max-width: 640px) {
  .hero-garland {
    display: none;
  }
}

@media (max-width: 980px) {
  .hero {
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
