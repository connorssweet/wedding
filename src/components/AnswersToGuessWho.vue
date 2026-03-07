<script setup lang="ts">
import BowtieIcon from './icons/BowtieIcon.vue'
import RingIcon from './icons/RingIcon.vue'

type GuessWhoItem = {
  question: string
  answer: 'bride' | 'groom'
}

defineProps<{
  items: GuessWhoItem[]
}>()
</script>

<template>
  <section class="section guess-who" id="guess-who-answers">
    <h2>Answ<span class="custom-spacing">e</span>rs to Guess Who</h2>

    <div class="answers-card">
      <article v-for="item in items" :key="item.question" class="answer-row">
        <p class="answer-question">{{ item.question }}</p>
        <div class="answer-icons">
          <span
            class="answer-icon"
            :class="{ 'answer-icon--active': item.answer === 'bride' }"
            aria-label="Bride"
            title="Bride"
          >
            <RingIcon />
          </span>

          <span
            class="answer-icon"
            :class="{ 'answer-icon--active': item.answer === 'groom' }"
            aria-label="Groom"
            title="Groom"
          >
            <BowtieIcon />
          </span>
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.guess-who {
  display: grid;
  gap: calc(var(--space) * 1.5);
}

.answers-card {
  background: var(--paper);
  border: 1px solid var(--line);
  border-radius: calc(var(--space) * 2);
  padding: calc(var(--space) * 2.25);
  box-shadow: 0 10px 22px rgba(0, 0, 0, 0.05);
  display: grid;
  gap: calc(var(--space) * 1.1);
}

.answer-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: calc(var(--space) * 1.5);
  padding: calc(var(--space) * 0.75) 0;
  border-bottom: 1px solid var(--line);
}

.answer-row:last-child {
  border-bottom: 0;
}

.answer-question {
  margin: 0;
  font-size: 20px;
}

.answer-icons {
  display: inline-flex;
  gap: calc(var(--space) * 0.75);
  flex-shrink: 0;
}

.answer-icon {
  width: 52px;
  height: 34px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  color: rgba(34, 49, 29, 0.35);
  transition: transform 160ms ease, color 160ms ease;
}

.answer-icon svg {
  width: 100%;
  height: 100%;
}

.answer-icon--active {
  color: var(--ink);
  transform: scale(1.05);
}

@media (max-width: 720px) {
  .answer-row {
    flex-direction: column;
    align-items: flex-start;
    gap: calc(var(--space) * 0.7);
  }
}
</style>
