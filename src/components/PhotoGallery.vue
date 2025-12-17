<script setup lang="ts">
type Photo = {
  src: string
}

defineProps<{
  photos: Photo[]
}>()
</script>

<template>
  <section class="section" id="photos">
    <div class="photo-grid" role="list">
      <div v-for="photo in photos" :key="photo.src" class="photo-card" role="listitem" tabindex="0">
        <img
          :src="photo.src"
          loading="lazy"
          decoding="async"
          width="900"
          height="1200"
          sizes="(max-width: 900px) 33vw, 300px"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.photo-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: calc(var(--space) * 1.75);
  margin-top: calc(var(--space) * 3.5);
}

.photo-card {
  position: relative;
  padding: 0;
  border: 1px solid var(--line);
  overflow: hidden;
  border-radius: calc(var(--space) * 2);
  background: var(--paper);
  transition: transform 160ms ease, box-shadow 160ms ease, border-color 160ms ease;
  content-visibility: auto;
  contain-intrinsic-size: 400px 533px;
}

.photo-card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  aspect-ratio: 3 / 4;
}

.photo-card:hover {
  transform: scale(1.03);
  box-shadow: 0 12px 26px rgba(0, 0, 0, 0.08);
  border-color: rgba(31, 25, 21, 0.16);
}

.photo-card:focus-visible,
.photo-card:active {
  transform: scale(1.02);
  border-color: rgba(31, 25, 21, 0.2);
  box-shadow: 0 12px 26px rgba(0, 0, 0, 0.08);
}

@media (max-width: 640px) {
  .photo-grid {
    grid-template-columns: 1fr;
    gap: calc(var(--space) * 1.25);
  }
}
</style>
