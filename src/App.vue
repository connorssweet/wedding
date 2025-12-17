<script setup lang="ts">
import HeroSection from './components/HeroSection.vue'
import PhotoGallery from './components/PhotoGallery.vue'
import StorySection from './components/StorySection.vue'
import ScheduleSection from './components/ScheduleSection.vue'
import RsvpSection from './components/RsvpSection.vue'
import PageFooter from './components/PageFooter.vue'

type Photo = {
  src: string
}

type ScheduleItem = {
  title: string
  time: string
  location: string
  detail?: string
}

const photos: Photo[] = [
  { src: 'photos/engagement-photo-1.jpg' },
  { src: 'photos/engagement-photo-2.jpg' },
  { src: 'photos/engagement-photo-3.jpg' },
  { src: 'photos/engagement-photo-4.jpg' },
  { src: 'photos/engagement-photo-5.jpg' },
  { src: 'photos/engagement-photo-6.jpg' },
  { src: 'photos/engagement-photo-7.jpg' },
  { src: 'photos/engagement-photo-8.jpg' },
  { src: 'photos/engagement-photo-9.jpg' }
]

const schedule: ScheduleItem[] = [
  { title: 'Ceremony', time: '5:30 PM - 6:00 PM', location: 'Pavilion' },
  { title: 'Cocktail Hour', time: '6:00 PM - 7:00 PM', location: 'Garden Terrace' },
  { title: 'Reception', time: '6:00 PM - 1:30 AM', location: 'Waterfront Room' }
]

const storyParagraphs = [
  "Connor first laid eyes on Laura in their high school geography class in January 2014. He was immediately drawn to her immense coolness, and her ability to stay within the lines while colouring a map of Canada. Laura, on the other hand, couldn't help but notice Connor's unique sense of style, particularly his collection of vests.",
  'Ten years passed, and their love only grew stronger. Finally, in June 2024, during a romantic trip to Italy, Connor got down on one knee on the coast of Capri and asked Laura to be his wife.',
  "Now, as they plan their future together, Connor and Laura are more in love than ever. They can't wait to start this new chapter of their lives as husband and wife, knowing that their love story is just beginning."
]

const rsvpLink = 'https://forms.gle/example'

const scrollToSection = (id: string) => {
  const target = document.getElementById(id)
  if (target) {
    target.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>

<template>
  <main class="page">
    <HeroSection
      title="Connor & Laura"
      subtitle="invite you to their wedding"
      date-main="March 14, 2026"
      date-small="3.14.2026"
      @scroll-rsvp="scrollToSection('rsvp')"
      @scroll-schedule="scrollToSection('schedule')"
    />

    <PhotoGallery :photos="photos" />

    <StorySection
      title="Our story"
      subtitle="A tale over ten years in the making"
      :paragraphs="storyParagraphs"
    />

    <ScheduleSection
      :schedule="schedule"
      venue-name="The Cambridge Mill"
      venue-address="100 Water St N, Cambridge, ON"
    />

    <RsvpSection :rsvp-link="rsvpLink" />

    <PageFooter message="We are so excited to see you there." @back-to-top="scrollToTop" />
  </main>
</template>
