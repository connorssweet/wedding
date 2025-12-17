<script setup lang="ts">
defineProps<{
  title: string
  subtitle: string
  paragraphs: string[]
}>()
</script>

<template>
  <section class="section story" id="story">
    <div class="section-header">
      <div>
        <h2>{{ title }}</h2>
        <p class="muted">{{ subtitle }}</p>
      </div>
    </div>
    <div class="story-content">
      <p v-for="paragraph in paragraphs" :key="paragraph">
        {{ paragraph }}
      </p>
    </div>
  </section>
</template>

<style scoped>
.story-content {
  margin-top: calc(var(--space) * 3.25);
  display: grid;
  gap: calc(var(--space) * 2.25);
  font-size: 18px;
  line-height: 1.8;
}
</style>
