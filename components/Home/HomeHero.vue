<template>
  <div class="pt-20">
    <div class="def-container def-padding-full">
      <h1 class="md:text-8xl text-4xl text-boss max-w-5xl w-full">
        <Motion v-for="(word, index) in headingLetters" :key="index" class="inline-block mr-2"
          :initial="{ opacity: 0, y: 20, rotateX: -90 }" :animate="{ opacity: 1, y: 0, rotateX: 0 }" :transition="{
            duration: 0.6,
            delay: 0.4 + (index * 0.08),
            ease: 'backOut'
          }" :whileHover="{
            y: -5,
            scale: 1.05,
            color: '#95afb8',
            transition: { duration: 0.2 }
          }">
          {{ word }}
        </Motion>
      </h1>
      <div class="my-16 relative">
        <img src="/Hero/heroMainBg.png" alt="">
        <div
          class="absolute md:top-10 top-3 md:left-10 left-3 p-5 bg-[#ffffff3c] backdrop-blur-lg text-black lg:text-3xl text-2xl max-w-[700px] rounded-2xl overflow-hidden">
          <Motion v-for="(word, index) in paraLetters" :key="index" class="inline-block mr-2"
            :initial="{ opacity: 0, y: 20, rotateX: -90 }" :animate="{ opacity: 1, y: 0, rotateX: 0 }" :transition="{
              duration: 0.6,
              delay: 1 + (index * 0.08),
              ease: 'backOut'
            }" :whileHover="{
            y: -5,
            scale: 1.05,
            color: '#95afb8',
            transition: { duration: 0.2 }
          }">
            {{ word }}
          </Motion>
        </div>
        <!-- Round Element with separate handlers -->
        <img src="/Hero/roundElement.webp" class="absolute -top-1/4 right-1/9 lg:h-56 w-fit md:h-40 h-24" alt="" :style="{
          transition: `all ${bounceEase}`,
          transform: roundElementVisible ?
            'translateX(0) translateY(0) rotate(0deg) scale(1)' :
            'translateX(100px) translateY(-100px) rotate(-180deg) scale(0)',
          opacity: roundElementVisible ? 1 : 0
        }" @mouseenter="onHover" @mouseleave="onLeave" @click="triggerRoundElementAnimation">

        <!-- Poly Element with separate handlers -->
        <img src="/Hero/polyElement.webp" class="absolute top-1/3 -left-1/12 lg:h-28 w-fit md:h-20 h-16" alt="" :style="{
          transition: `all ${bounceEase}`,
          transform: polyElementVisible ?
            'translateX(0) translateY(0) rotate(0deg) scale(1)' :
            'translateX(-100px) translateY(100px) rotate(180deg) scale(0)',
          opacity: polyElementVisible ? 1 : 0
        }" @mouseenter="onHover" @mouseleave="onLeave" @click="triggerPolyElementAnimation">
      </div>
    </div>
  </div>
</template>

<script setup>
import { spring } from 'motion-v'
import { ref, onMounted } from 'vue'

// Split paragraph into headingLetters for animation
const headingText = "Transforming Visions into Digital Realities"
const headingLetters = computed(() => headingText.split(' '))
const paraText = "CodesHawk delivers cutting-edge web, AI, and digital marketing solutions that propel your business forward."
const paraLetters = computed(() => paraText.split(' '))

// Separate animation states for each image
const roundElementVisible = ref(false)
const polyElementVisible = ref(false)
const isHovered = ref(false)

// Spring easing for smooth bouncy animation
const bounceEase = spring(0.6, 0.7)
const hoverEase = spring(0.8, 0.9)

// Trigger entrance animations on mount with different delays
onMounted(() => {
  // Round element appears first
  setTimeout(() => {
    roundElementVisible.value = true
  }, 800)

  // Poly element appears slightly later
  setTimeout(() => {
    polyElementVisible.value = true
  }, 1200)
})

// Interactive handlers (same for both images)
const onHover = (event) => {
  isHovered.value = true

  // Get element and cursor positions
  const rect = event.target.getBoundingClientRect()
  const elementCenterX = rect.left + rect.width / 2
  const elementCenterY = rect.top + rect.height / 2
  const cursorX = event.clientX
  const cursorY = event.clientY

  // Calculate direction from cursor to element center
  const deltaX = elementCenterX - cursorX
  const deltaY = elementCenterY - cursorY

  // Normalize and scale the movement (move away from cursor)
  const distance = Math.sqrt(deltaX * deltaX + deltaY * deltaY)
  const moveDistance = 30 // How far to move away
  const moveX = (deltaX / distance) * moveDistance
  const moveY = (deltaY / distance) * moveDistance

  event.target.style.transition = `transform ${hoverEase}`
  event.target.style.transform = `translateX(${moveX}px) translateY(${moveY}px) rotate(15deg) scale(1.05)`
}

const onLeave = (event) => {
  isHovered.value = false
  event.target.style.transition = `transform ${bounceEase}`
  event.target.style.transform = 'translateX(0) translateY(0) rotate(0deg) scale(1)'
}

// Separate click handlers for each image
const triggerRoundElementAnimation = () => {
  console.log('Round element clicked!')
  roundElementVisible.value = false
  setTimeout(() => {
    roundElementVisible.value = true
  }, 300)
}

const triggerPolyElementAnimation = () => {
  console.log('Poly element clicked!')
  polyElementVisible.value = false
  setTimeout(() => {
    polyElementVisible.value = true
  }, 300)
}

// You can also add specific animations for each element
const spinRoundElement = () => {
  // Custom animation for round element
  roundElementVisible.value = false
  setTimeout(() => {
    roundElementVisible.value = true
    // Add some special effect here if needed
  }, 200)
}

const bouncePolyElement = () => {
  // Custom animation for poly element
  polyElementVisible.value = false
  setTimeout(() => {
    polyElementVisible.value = true
    // Add some special effect here if needed
  }, 250)
}
</script>