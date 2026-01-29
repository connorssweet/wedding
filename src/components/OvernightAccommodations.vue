<script setup lang="ts">
import BaseButton from './BaseButton.vue'

const openMap = () => {
  window.open(
    'https://maps.google.com/?q=Cambridge%20Hotel%20%26%20Conference%20Centre%20700%20Hespeler%20Rd%20Cambridge%20ON%20N3H%205L8',
    '_blank',
    'noreferrer'
  )
}
</script>

<template>
  <section class="section accommodations" id="accommodations">
    <h2>Accommodations</h2>
    <div class="section-header accommodations-header">
      <div class="venue-note">
        <span class="venue-name">Cambridge Hotel & Conference Centre</span>
        <span class="venue-address muted">700 Hespeler Rd, Cambridge, ON N3H 5L8</span>
      </div>
      <BaseButton class="venue-map-btn" variant="primary" type="button" @click="openMap">
        View on Google Maps
      </BaseButton>
    </div>

    <article class="accommodations-card">
      <div class="accommodations-body">
        <h3 class="booking-deadline">Booking deadline: February 14, 2026</h3>
        <p class="booking-actions">
          Call
          <a class="contact-link" href="tel:+15196221505" target="_blank" rel="noreferrer">(519) 622-1505</a>
          or Email
          <a
            class="contact-link"
            href="mailto:frontdesk1@cambridgehotel.ca"
            target="_blank"
            rel="noreferrer"
          >
            frontdesk1@cambridgehotel.ca
          </a>
        </p>
        <p class="booking-detail">Mention the "Juodvirsis and Sweet Wedding" to receive the discounted rate.</p>
        <p class="booking-detail">Bookings after the deadline are subject to availability.</p>
      </div>
    </article>
  </section>
</template>

<style scoped>
.booking-detail {
  margin: 0;
}

.accommodations {
  display: grid;
  gap: calc(var(--space) * 3);
}

.accommodations-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: calc(var(--space) * 1.5);
  flex-wrap: wrap;
}

.venue-note {
  display: grid;
  gap: calc(var(--space) * 0.25);
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

.accommodations-card {
  background: var(--paper);
  border: 1px solid var(--line);
  border-radius: calc(var(--space) * 2.25);
  padding: calc(var(--space) * 2.75) calc(var(--space) * 3.25);
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.06);
  display: grid;
  gap: calc(var(--space) * 1.5);
  transition: transform 160ms ease, box-shadow 160ms ease, border-color 160ms ease;
}

.accommodations-card:hover {
  transform: scale(1.03);
  box-shadow: 0 16px 32px rgba(0, 0, 0, 0.08);
  border-color: rgba(31, 25, 21, 0.16);
}

.accommodations-card:focus-within,
.accommodations-card:active {
  transform: scale(1.015);
  box-shadow: 0 12px 26px rgba(0, 0, 0, 0.08);
  border-color: rgba(31, 25, 21, 0.14);
}

.accommodations-body {
  display: grid;
  gap: calc(var(--space));
}

.booking-deadline {
  margin: 0;
  font-size: 22px;
  font-family: 'London', 'Times New Roman', serif;
}

.booking-actions {
  margin: 0;
  display: flex;
  flex-wrap: wrap;
  gap: calc(var(--space) * 0.5);
  font-size: 20px;
  align-items: center;
}

.contact-link {
  color: var(--ink);
  font-weight: 700;
  text-decoration: underline;
  letter-spacing: 0.01em;
}

@media (max-width: 860px) {
  .accommodations-header {
    flex-direction: column;
    align-items: flex-start;
  }

  .venue-map-btn {
    align-self: flex-start;
  }
}

h3{
  font-family: 'London', 'Times New Roman', serif;
}
</style>
