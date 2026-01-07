<template>
  <section class="section faq" id="faq">
    <div class="section-header">
      <h2>Questions</h2>
    </div>
    <div class="faq-grid">
      <article v-for="item in faqs" :key="item.question" class="faq-item">
        <h3>{{ item.question }}</h3>
        <p>{{ item.answer }}</p>
        <div v-if="item.showSwatches" class="swatches">
          <span class="swatch swatch-forest" aria-label="Forest green"></span>
          <span class="swatch swatch-chocolate" aria-label="Chocolate brown"></span>
          <span class="swatch swatch-bronze" aria-label="Bronze"></span>
        </div>
      </article>
    </div>
    <p class="faq-contact">
      If you have any further questions, please feel free to reach out to
      <a href="mailto:connor.s.sweet@gmail.com" target="_blank" rel="noreferrer">Connor</a> or
      <a href="mailto:juodvirsis1999@gmail.com" target="_blank" rel="noreferrer">Laura</a>.
    </p>
  </section>
</template>

<style scoped>
.faq {
  display: grid;
  gap: calc(var(--space) * 3);
}

.faq-grid {
  display: grid;
  gap: calc(var(--space) * 2);
}

.faq-item h3 {
  margin: 0 0 calc(var(--space) * 0.5);
  font-size: 24px;
  font-family: 'London', 'Times New Roman', serif;
  font-weight: 700;
}

.faq-item p {
  margin: 0;
  font-size: 20px;
}

.swatches {
  display: flex;
  gap: calc(var(--space));
  margin-top: calc(var(--space) * 1.25);
}

.swatch {
  width: 38px;
  height: 38px;
  border-radius: 8px;
  border: 1px solid var(--line);
}

.swatch-forest {
  background: var(--ink);
}

.swatch-chocolate {
  background: var(--chocolate);
}

.swatch-bronze {
  background: var(--bronze);
}

.faq-contact {
  font-size: 20px;
  margin: calc(var(--space) * 3) 0 0;
}

.faq-contact a {
  color: var(--ink);
  font-weight: 700;
  text-decoration: underline;
}
</style>
<script setup lang="ts">
type FaqItem = {
  question: string
  answer: string
  showSwatches?: boolean
}

defineProps<{
  faqs: FaqItem[]
}>()
</script>
