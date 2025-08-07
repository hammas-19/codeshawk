<!-- GlobalAnimatedBlobs.vue - Single instance that changes colors -->
<script setup>
import { motion, useMotionValue, useSpring } from 'motion-v'
import { onMounted, ref, computed } from 'vue'

// Props for controlling the blobs from parent
const props = defineProps({
  activeSection: {
    type: String,
    default: 'section1'
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

// Color configurations for different sections
const sectionColors = {
  section1: {
    blob1: ['#cdf68b', '#fffff2', '#000000'],
    blob2: ['#000000', '#cdf68b', '#8b0000']
  },
  section2: {
    blob1: ['#0066ff', '#003d99', '#001a4d'],
    blob2: ['#ffff00', '#ffd700', '#ff8c00']
  },
  section3: {
    blob1: ['#8a2be2', '#9932cc', '#4b0082'],
    blob2: ['#ff69b4', '#ff1493', '#c71585']
  },
  section4: {
    blob1: ['#00ff88', '#00cc66', '#009944'],
    blob2: ['#00ffcc', '#00ddaa', '#00bb88']
  }
}

// Computed styles that change based on active section
const blob1Style = computed(() => {
  const colors = sectionColors[props.activeSection]?.blob1 || sectionColors.section1.blob1
  return {
    width: '500px',
    height: '500px',
    background: `radial-gradient(circle, ${colors.join(', ')})`,
    filter: 'blur(80px)',
    opacity: 0.6
  }
})

const blob2Style = computed(() => {
  const colors = sectionColors[props.activeSection]?.blob2 || sectionColors.section1.blob2
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