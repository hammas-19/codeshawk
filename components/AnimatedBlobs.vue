<!-- AnimatedBlobs.vue - Reusable Component -->
<script setup>
import { motion, useMotionValue, useSpring } from 'motion-v'
import { onMounted, computed, onUnmounted } from 'vue'

const props = defineProps({
  // Blob colors
  blob1Colors: {
    type: Array,
    default: () => ['#ff006e', '#8338ec', '#3a86ff']
  },
  blob2Colors: {
    type: Array,
    default: () => ['#ff7b00', '#ff006e', '#8338ec']
  },

  // Blob sizes
  blob1Size: {
    type: Number,
    default: 500
  },
  blob2Size: {
    type: Number,
    default: 400
  },

  // Animation settings
  blob1Stiffness: {
    type: Number,
    default: 20
  },
  blob1Damping: {
    type: Number,
    default: 30
  },
  blob2Stiffness: {
    type: Number,
    default: 15
  },
  blob2Damping: {
    type: Number,
    default: 35
  },

  // Visual settings
  blurAmount: {
    type: Number,
    default: 80
  },
  opacity: {
    type: Number,
    default: 0.6
  },

  // Container overflow
  overflow: {
    type: String,
    default: 'hidden'
  }
})

// Get or create global mouse position (shared across all instances)
let globalMouseX, globalMouseY

if (process.client) {
  // Check if global mouse values already exist
  if (!window.globalMouseX) {
    window.globalMouseX = useMotionValue(window.innerWidth / 2)
    window.globalMouseY = useMotionValue(window.innerHeight / 2)
  }
  globalMouseX = window.globalMouseX
  globalMouseY = window.globalMouseY
} else {
  // Fallback for SSR
  globalMouseX = useMotionValue(0)
  globalMouseY = useMotionValue(0)
}

// Spring-animated blob positions using global mouse
const blob1X = useSpring(globalMouseX, {
  stiffness: props.blob1Stiffness,
  damping: props.blob1Damping
})
const blob1Y = useSpring(globalMouseY, {
  stiffness: props.blob1Stiffness,
  damping: props.blob1Damping
})

const blob2X = useSpring(globalMouseX, {
  stiffness: props.blob2Stiffness,
  damping: props.blob2Damping
})
const blob2Y = useSpring(globalMouseY, {
  stiffness: props.blob2Stiffness,
  damping: props.blob2Damping
})

// Computed styles for blobs
const blob1Style = computed(() => ({
  width: `${props.blob1Size}px`,
  height: `${props.blob1Size}px`,
  background: `radial-gradient(circle, ${props.blob1Colors.join(', ')})`,
  filter: `blur(${props.blurAmount}px)`,
  opacity: props.opacity
}))

const blob2Style = computed(() => ({
  width: `${props.blob2Size}px`,
  height: `${props.blob2Size}px`,
  background: `radial-gradient(circle, ${props.blob2Colors.join(', ')})`,
  filter: `blur(${props.blurAmount}px)`,
  opacity: props.opacity
}))

let mouseMoveHandler

onMounted(() => {
  if (process.client) {
    // Create global mouse move handler if it doesn't exist
    if (!window.globalMouseMoveHandler) {
      window.globalMouseMoveHandler = (e) => {
        window.globalMouseX.set(e.clientX)
        window.globalMouseY.set(e.clientY)
      }
      document.addEventListener('mousemove', window.globalMouseMoveHandler)
    }

    mouseMoveHandler = window.globalMouseMoveHandler
  }
})

onUnmounted(() => {
  // Don't remove the global handler when component unmounts
  // It should persist across all AnimatedBlobs instances
})
</script>

<template>
  <div class="animated-blobs-container" :style="{ overflow: overflow }">
    <!-- Blobs -->
    <div class="blobs-wrapper">
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

    <!-- Slot for content -->
    <div class="content-slot">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.animated-blobs-container {
  position: relative;
  width: 100%;
  height: 100%;
  /* Use default cursor, not custom */
}

.blobs-wrapper {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 1;
}

.blob {
  position: fixed;
  border-radius: 50%;
  pointer-events: none;
  will-change: transform;
  transition: background 0.8s ease, opacity 0.8s ease;
}

.content-slot {
  position: relative;
  z-index: 10;
  pointer-events: none;
  width: 100%;
  height: 100%;
}

.content-slot :deep(*) {
  pointer-events: auto;
}

@media (max-width: 768px) {
  .blob {
    /* Smaller blobs on mobile */
    transform: scale(0.7) translate(-60%, -60%);
  }
}
</style>