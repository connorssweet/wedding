<script setup lang="ts">
type ScheduleItem = {
  title: string
  time: string
  location: string
}

defineProps<{
  schedule: ScheduleItem[]
  venueName: string
  venueAddress: string
}>()
</script>

<template>
  <section class="section schedule" id="schedule">
    <div class="section-header schedule-header">
      <div>
        <h2>Schedule</h2>
        <div class="venue-note">
          <span class="venue-name">{{ venueName }}</span>
          <span class="venue-address muted">{{ venueAddress }}</span>
        </div>
      </div>
    </div>
    <div class="schedule-grid">
      <article v-for="item in schedule" :key="item.title" class="schedule-item">
        <p class="schedule-time">{{ item.time }}</p>
        <h3 class="schedule-title">{{ item.title }}</h3>
        <p class="schedule-location">{{ item.location }}</p>
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
  font-size: 14px;
}

.venue-name {
  font-weight: 700;
}

.venue-address {
  font-size: 14px;
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
  transform: scale(1.02);
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
  color: #8f857c;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  font-weight: 700;
  font-size: 11px;
}

.schedule-title {
  margin: 0 0 calc(var(--space));
  font-weight: 600;
}

.schedule-location {
  margin: 0 0 calc(var(--space) * 0.75);
}
</style>
