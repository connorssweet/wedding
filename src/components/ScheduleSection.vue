<script setup lang="ts">
import BaseButton from './BaseButton.vue'

type ScheduleItem = {
  title: string
  time: string
  location: string
  detail?: string
  subEvents?: { title: string; time: string; location?: string; detail?: string }[]
}

defineProps<{
  schedule: ScheduleItem[]
  venueName: string
  venueAddress: string
}>()

const openMap = () => {
  window.open(
    'https://maps.google.com/?q=The%20Cambridge%20Mill%20100%20Water%20St%20N%20Cambridge%20ON',
    '_blank',
    'noreferrer'
  )
}
</script>

<template>
  <section class="section schedule" id="schedule">
    <h2>Schedule</h2>
    <div class="section-header schedule-header">
      <div>
        <div class="venue-note">
          <span class="venue-name">{{ venueName }}</span>
          <span class="venue-address muted">{{ venueAddress }}</span>
        </div>
      </div>
      <BaseButton
        class="venue-map-btn"
        variant="primary"
        type="button"
        @click="openMap"
      >
        View on Google Maps
      </BaseButton>
    </div>
    <div class="schedule-grid">
      <article v-for="item in schedule" :key="item.title" class="schedule-item">
        <p class="schedule-time">{{ item.time }}</p>
        <h3 class="schedule-title">{{ item.title }}</h3>
        <p class="muted schedule-location">{{ item.location }}</p>
        <p v-if="item.detail" class="schedule-note">{{ item.detail }}</p>
        <ul v-if="item.subEvents?.length" class="schedule-sublist">
          <li v-for="sub in item.subEvents" :key="sub.title" class="schedule-subitem">
            <div class="schedule-subtime">{{ sub.time }}</div>
            <div class="schedule-subcontent">
              <span class="schedule-subtitle">{{ sub.title }}</span>
              <span v-if="sub.location" class="muted schedule-sublocation">{{ sub.location }}</span>
              <span v-if="sub.detail" class="muted schedule-subdetail">{{ sub.detail }}</span>
            </div>
          </li>
        </ul>
      </article>
    </div>
  </section>
</template>

<style scoped>
.schedule-header {
  justify-content: space-between;
  align-items: center;
  gap: calc(var(--space) * 1.5);
}

.venue-note {
  margin-top: var(--space);
  display: grid;
  gap: calc(var(--space) * 0.25);
  font-size: 20px;
}

.venue-name {
  font-weight: 700;
  font-size: 22px;
}

.venue-address {
  font-size: 20px;
}

.venue-map-btn {
  white-space: nowrap;
}

.schedule-grid {
  margin-top: calc(var(--space) * 3.5);
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: calc(var(--space) * 1.75);
}

.schedule-item {
  background: var(--paper);
  border-radius: calc(var(--space) * 2);
  padding: calc(var(--space) * 2.25);
  border: 1px solid var(--line);
  box-shadow: 0 10px 22px rgba(0, 0, 0, 0.05);
  transition: transform 160ms ease, box-shadow 160ms ease, border-color 160ms ease;
}

.schedule-item:hover {
  transform: scale(1.03);
  box-shadow: 0 16px 32px rgba(0, 0, 0, 0.08);
  border-color: rgba(31, 25, 21, 0.16);
}

.schedule-item:focus-within,
.schedule-item:active {
  transform: scale(1.015);
  box-shadow: 0 12px 26px rgba(0, 0, 0, 0.08);
  border-color: rgba(31, 25, 21, 0.14);
}

.schedule-time {
  margin: 0 0 calc(var(--space) * 0.75);
  color: var(--muted);
  letter-spacing: 0.12em;
  text-transform: uppercase;
  font-weight: 700;
  font-size: 20px;
}

.schedule-title {
  margin: 0 0 calc(var(--space));
  font-weight: 600;
  font-size: 22px;
}

.schedule-location {
  margin: 0 0 calc(var(--space) * 0.75);
  font-size: 20px;
  display: block;
}

.schedule-sublist {
  list-style: none;
  padding: calc(var(--space)) calc(var(--space) * 1.25) 0;
  margin: calc(var(--space) * 1) 0 0;
  border-top: 1px solid var(--line);
  display: grid;
  gap: calc(var(--space) * 0.75);
}

.schedule-subitem {
  display: grid;
  grid-template-columns: 140px 1fr;
  gap: calc(var(--space));
  align-items: start;
}

.schedule-subtime {
  font-weight: 700;
  letter-spacing: 0.02em;
  color: var(--ink);
  font-size: 20px;
}

.schedule-subtitle {
  font-weight: 600;
  font-size: 20px;
}

.schedule-sublocation,
.schedule-subdetail {
  display: block;
  font-size: 20px;
}

.schedule-note {
  margin-top: calc(var(--space));
  padding-top: calc(var(--space));
  border-top: 1px solid var(--line);
}

h3{
  font-family: 'London', 'Times New Roman', serif;
}
</style>
