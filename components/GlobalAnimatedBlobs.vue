<!-- GlobalAnimatedBlobs.vue - Updated for your components -->
<script setup>
import { motion, useMotionValue, useSpring } from 'motion-v'
import { onMounted, ref, computed } from 'vue'

// Props for controlling the blobs from parent
const props = defineProps({
  activeSection: {
    type: String,
    default: 'homeHero'
  }
})

// Global mouse position
const mouseX = useMotionValue(0)
const mouseY = useMotionValue(0)

// Spring-animated blob positions
const blob1X = useSpring(mouseX, { stiffness: 20, damping: 30 })
const blob1Y = useSpring(mouseY, { stiffness: 20, damping: 30 })

const blob2X = useSpring(mouseX, { stiffness: 15, damping: 35 })
const blob2Y = useSpring(mouseY, { stiffness: 15, damping: 35 })

// 🎨 COLOR CONFIGURATIONS FOR YOUR COMPONENTS 🎨
const sectionColors = {
  homeHero: {
    blob1: ['#bbb3ff', '#9385ff', '#6652ff'],      // Pink to blue gradient (energetic hero)
    blob2: ['#ffe7d1', '#ffbe85', '#ff8a24']       // Orange to purple gradient
  },
  homeWhy: {
    blob1: ['#e6e6e6', '#cccccc', '#969696'],      // Cyan to blue (trust/reliability)
    blob2: ['#b9cfcf', '#a1bebf', '#76a1a2']       // Green gradient (growth/positive)
  },
  homeDifference: {
    blob1: ['#bbb3ff', '#9385ff', '#6652ff'],      // Red gradient (bold difference)
    blob2: ['#ffa502', '#ff6348', '#ff4757']       // Orange to red gradient
  },
  homeServices: {
    blob1: ['#7b68ee', '#9370db', '#6a5acd'],      // Purple gradient (professional)
    blob2: ['#20bf6b', '#26de81', '#2ed573']       // Green gradient (services/solutions)
  },
  homeStats: {
    blob1: ['#f39c12', '#e67e22', '#d35400'],      // Orange gradient (achievement)
    blob2: ['#3498db', '#2980b9', '#2471a3']       // Blue gradient (data/trust)
  },
  homeTeam: {
    blob1: ['#e74c3c', '#c0392b', '#a93226'],      // Red gradient (passion/energy)
    blob2: ['#9b59b6', '#8e44ad', '#7d3c98']       // Purple gradient (creativity)
  },
  testimonials: {
    blob1: ['#2ecc71', '#27ae60', '#229954'],      // Green gradient (positive feedback)
    blob2: ['#e6e6e6', '#cccccc', '#969696']       // Yellow to orange (happiness/satisfaction)
  }
}

// Computed styles that change based on active section
const blob1Style = computed(() => {
  const colors = sectionColors[props.activeSection]?.blob1 || sectionColors.homeHero.blob1
  return {
    width: '500px',
    height: '500px',
    background: `radial-gradient(circle, ${colors.join(', ')})`,
    filter: 'blur(80px)',
    opacity: 0.6
  }
})

const blob2Style = computed(() => {
  const colors = sectionColors[props.activeSection]?.blob2 || sectionColors.homeHero.blob2
  return {
    width: '400px',
    height: '400px',
    background: `radial-gradient(circle, ${colors.join(', ')})`,
    filter: 'blur(80px)',
    opacity: 0.6
  }
})

function handleMouseMove(e) {
  mouseX.set(e.clientX)
  mouseY.set(e.clientY)
}

onMounted(() => {
  // Set initial position
  mouseX.set(window.innerWidth / 2)
  mouseY.set(window.innerHeight / 2)

  // Add global mouse listener
  document.addEventListener('mousemove', handleMouseMove)
})
</script>

<template>
  <!-- Global blobs that appear on top of all content -->
  <div class="global-blobs-container">
    <!-- Blob 1 -->
    <motion.div class="blob" :style="{
      ...blob1Style,
      left: blob1X,
      top: blob1Y,
      transform: 'translate(-60%, -60%)'
    }" />

    <!-- Blob 2 -->
    <motion.div class="blob" :style="{
      ...blob2Style,
      left: blob2X,
      top: blob2Y,
      transform: 'translate(-40%, -40%)'
    }" />
  </div>
</template>

<style scoped>
.global-blobs-container {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 1;
}

.blob {
  position: fixed;
  border-radius: 50%;
  pointer-events: none;
  will-change: transform;
  transition: background 0.8s ease;
}
</style>