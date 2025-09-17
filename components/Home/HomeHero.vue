<template>
  <div class="pt-10 overflow-hidden">
    <div class="def-container lg:def-padding-full">
      <h1 class="md:text-8xl text-4xl text-boss max-w-5xl w-full">
        <Motion v-for="(word, index) in headingLetters" :key="index" class="inline-block mr-2"
          :initial="{ opacity: 0, y: 20, rotateX: -90 }" :animate="{ opacity: 1, y: 0, rotateX: 0 }" :transition="{
            duration: 0.6,
            delay: 0.4 + (index * 0.08),
            ease: 'backOut'
          }" :while-hover="{
            y: -5,
            scale: 1.05,
            color: '#95afb8',
            transition: { duration: 0.2 }
          }">
          {{ word }}
        </Motion>
      </h1>
      <div class="my-16 relative h-[calc(100vh-400px)] lg:min-h-[600px]">
        <div class="h-[50px] md:w-[340px] w-[175px] absolute bottom-0 md:left-0 right-0  backdrop-blur-lg rounded-2xl  flex items-center md:gap-3 gap-1">
          <div class="flex -space-x-4 rtl:space-x-reverse">
            <img class="md:w-12 w-5 md:h-12 h-5 border-white rounded-full object-cover border-2 border-white"
              src="https://images.unsplash.com/photo-1590098446345-7d26046c81b7?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8N3x8UGFraXN0YW5pJTIwcHJvZmlsZSUyMGltYWdlfGVufDB8fDB8fHww"
              alt="">
            <img class="md:w-12 w-5 md:h-12 h-5 border-white rounded-full object-cover border-2 border-white"
              src="https://images.unsplash.com/photo-1654349560392-ecf800ed137c?q=80&w=686&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
              alt="">
            <img class="md:w-12 w-5 md:h-12 h-5 border-white rounded-full object-cover border-2 border-white"
              src="https://plus.unsplash.com/premium_photo-1706803193101-f10b46f97ef7?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDR8fHxlbnwwfHx8fHw%3D"
              alt="">
            <img class="md:w-12 w-5 md:h-12 h-5 border-white rounded-full object-cover border-2 border-white"
              src="https://images.unsplash.com/photo-1644056255024-e07640eb8c53?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE0fHx8ZW58MHx8fHx8"
              alt="">
          </div>
          <span class=" font-bold text-black md:text-4xl text-sm">2k+</span>
          <h3 class="text-black md:text-lg text-xs font-medium md:leading-5 leading-3 flex flex-col "><span>Satisfied</span> <span>Customes</span></h3>
        </div>
        <img src="https://blogger.googleusercontent.com/img/a/AVvXsEgDyNRsYXtClB-DtesRzAL1jmnonqkfJUzmPWFFbEu6vts9o973u3M_lZ21Af-2BImkteF0plrV0uIATpdB_OO5avWbZXDGrABUBVahnAzSO1_7Nnk9nkIrIV0qSmXG04FvTRrv8mkuyJZxOY_EZ-X7YYn3JDzF28uy0H85NVJlLKjK0hJzm_Kz49FzsEI=w640-h360" class="inverted-radius w-full lg:h-full h-[calc(100vh-400px)] lg:max-h-[600px] object-cover" alt="">
        <!-- <video autoplay loop
          class="inverted-radius border-2 w-full lg:h-full h-[calc(100vh-400px)] lg:max-h-[600px] object-cover">
          <source src="/vdv.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video> -->

        <div
          class="absolute md:top-10 top-3 md:left-10 left-3 md:p-5 p-3 mr-3 md:mr-0 bg-[#ffffff3c] backdrop-blur-lg text-black lg:text-3xl md:text-xl text-sm max-w-[700px] rounded-2xl overflow-hidden">
          <Motion v-for="(word, index) in paraLetters" :key="index" class="inline-block mr-2"
            :initial="{ opacity: 0, y: 20, rotateX: -90 }" :animate="{ opacity: 1, y: 0, rotateX: 0 }" :transition="{
              duration: 0.6,
              delay: 1 + (index * 0.08),
              ease: 'backOut'
            }" :while-hover="{
            y: -5,
            scale: 1.05,
            color: '#95afb8',
            transition: { duration: 0.2 }
          }">
            {{ word }}
          </Motion>
        </div>
        <!-- Round Element with separate handlers -->
        <img src="/Hero/roundElement.webp"
          class="absolute md:-top-1/4 top-1/4 md:right-1/9 -right-7 lg:h-56 w-fit md:h-40 h-24" alt="" :style="{
          transition: `all ${bounceEase}`,
          transform: roundElementVisible ?
            'translateX(0) translateY(0) rotate(0deg) scale(1)' :
            'translateX(100px) translateY(-100px) rotate(-180deg) scale(0)',
          opacity: roundElementVisible ? 1 : 0
        }" @mouseenter="onHover" @mouseleave="onLeave" @click="triggerRoundElementAnimation">

        <!-- Poly Element with separate handlers -->
        <img src="/Hero/polyElement.webp" class="absolute md:top-1/3 top-2/3 -left-1/12 lg:h-28 w-fit md:h-20 h-16"
          alt="" :style="{
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
<style scoped>

.inverted-radius {
  --r: 20px;
  /* the radius */
  --s: 30px;
  /* size of inner curve */
  --x: 300px;
  /* horizontal offset (no percentage) */
  --y: 10px;
  /* vertical offset (no percentage) */
  border-radius: var(--r);
  --_m: /calc(2*var(--r)) calc(2*var(--r)) radial-gradient(#000 70%, #0000 72%);
  --_g: conic-gradient(from 180deg at var(--r) calc(100% - var(--r)), #0000 25%, #000 0);
  --_d: (var(--s) + var(--r));
  mask:
    calc(var(--_d) + var(--x)) 100% var(--_m),
    0 calc(100% - var(--_d) - var(--y)) var(--_m),
    radial-gradient(var(--s) at 0 100%, #0000 99%, #000 calc(100% + 1px)) calc(var(--r) + var(--x)) calc(-1*var(--r) - var(--y)),
    var(--_g) calc(var(--_d) + var(--x)) 0,
    var(--_g) 0 calc(-1*var(--_d) - var(--y));
  mask-repeat: no-repeat;
}
@media (max-width: 768px) {
  .inverted-radius {
    --r: 15px;
    /* Adjust radius for smaller devices */
    --s: 25px;
    /* Adjust size of inner curve */
    --x: 140px;
    /* Adjust horizontal offset */
    --y: 8px;
    /* Adjust vertical offset */
    border-radius: var(--r);
      --_m: /calc(2*var(--r)) calc(2*var(--r)) radial-gradient(#000 70%, #0000 72%);
      --_g: conic-gradient(from 90deg at calc(100% - var(--r)) calc(100% - var(--r)), #0000 25%, #000 0);
      --_d: (var(--s) + var(--r));
      mask:
        calc(100% - var(--_d) - var(--x)) 100% var(--_m),
        100% calc(100% - var(--_d) - var(--y)) var(--_m),
        radial-gradient(var(--s) at 100% 100%, #0000 99%, #000 calc(100% + 1px)) calc(-1*var(--r) - var(--x)) calc(-1*var(--r) - var(--y)),
        var(--_g) calc(-1*var(--_d) - var(--x)) 0,
        var(--_g) 0 calc(-1*var(--_d) - var(--y));
      mask-repeat: no-repeat;
  }
}
</style>