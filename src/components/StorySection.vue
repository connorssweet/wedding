<script setup lang="ts">
defineProps<{
  title: string
  paragraphs: string[]
}>()
</script>

<template>
  <section class="section story" id="story">
    <div class="section-header">
      <div>
        <h2>{{ title }}</h2>
      </div>
    </div>
    <div class="muted story-content">
      <p v-for="paragraph in paragraphs" :key="paragraph">
        {{ paragraph }}
      </p>
    </div>
  </section>
</template>

<style scoped>
.story-content {
  display: grid;
}
</style>
