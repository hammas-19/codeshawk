<template>
  <div>
    <!-- Global blobs that change color based on active section -->
    <GlobalAnimatedBlobs :active-section="activeSection" />

    <!-- Your existing components with section detection -->
    <section ref="homeHero" data-section="homeHero">
      <HomeHero />
    </section>

    <section ref="homeWhy" data-section="homeWhy">
      <HomeWhy />
    </section>

    <section ref="homeDifference" data-section="homeDifference">
      <HomeDiffrence />
    </section>

    <section ref="homeServices" data-section="homeServices">
      <HomeServices />
    </section>

    <section ref="homeStats" data-section="homeStats">
      <HomeStats />
    </section>

    <section ref="homeTeam" data-section="homeTeam">
      <HomeTeam />
    </section>

    <section ref="testimonials" data-section="testimonials">
      <TheTestimonials />
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const activeSection = ref('homeHero')

// Section refs - one for each component
const homeHero = ref()
const homeWhy = ref()
const homeDifference = ref()
const homeServices = ref()
const homeStats = ref()
const homeTeam = ref()
const testimonials = ref()

let observer

onMounted(() => {
  // Create intersection observer to detect which section is active
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting && entry.intersectionRatio > 0.3) {
          const sectionName = entry.target.dataset.section
          if (sectionName) {
            activeSection.value = sectionName
            console.log('Active section:', sectionName) // For debugging
          }
        }
      })
    },
    {
      threshold: [0.3], // Trigger when 30% of section is visible
      rootMargin: '-10% 0px -10% 0px' // Add some margin for better detection
    }
  )

  // Observe all sections
  const sections = [
    homeHero.value,
    homeWhy.value,
    homeDifference.value,
    homeServices.value,
    homeStats.value,
    homeTeam.value,
    testimonials.value
  ]

  sections.forEach(section => {
    if (section) observer.observe(section)
  })
})

onUnmounted(() => {
  if (observer) {
    observer.disconnect()
  }
})
</script>

<style scoped>
/* Make sure sections are properly spaced and detectable */
section {
  position: relative;
  z-index: 10;
}

/* Optional: Add some debugging to see active sections */
section[data-section] {
  min-height: 50vh;
  /* Ensure sections have enough height for detection */
}
</style>