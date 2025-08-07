<script setup lang="ts">
import { motion, useMotionValue, useSpring } from 'motion-v'
import { onMounted, ref } from 'vue'

const sectionRef = ref()

// Motion values for pointer position
const mouseX = useMotionValue(0)
const mouseY = useMotionValue(0)

// Spring-animated blob positions - these will smoothly follow the mouse
const blob1X = useSpring(mouseX, { stiffness: 20, damping: 30 })
const blob1Y = useSpring(mouseY, { stiffness: 20, damping: 30 })

const blob2X = useSpring(mouseX, { stiffness: 15, damping: 35 })
const blob2Y = useSpring(mouseY, { stiffness: 15, damping: 35 })

function handleMouseMove(e) {
  // Update mouse position
  mouseX.set(e.clientX)
  mouseY.set(e.clientY)
}

onMounted(() => {
  // Set initial positions to center of screen
  const centerX = window.innerWidth / 2
  const centerY = window.innerHeight / 2

  mouseX.set(centerX)
  mouseY.set(centerY)
})
</script>

<template>
  <div ref="sectionRef" class="demo-section !overflow-hidden" @mousemove="handleMouseMove">
    <!-- Blobs - positioned behind content -->
    <div class="blobs-container">
      <!-- Blob 1 - Slower, offset behind cursor -->
      <motion.div class="blob blob-1" :style="{
        left: blob1X,
        top: blob1Y,
        transform: 'translate(-60%, -60%)'
      }" />

      <!-- Blob 2 - Even slower, different offset -->
      <motion.div class="blob blob-2" :style="{
        left: blob2X,
        top: blob2Y,
        transform: 'translate(-40%, -40%)'
      }" />
    </div>

    <!-- Content - positioned above blobs -->
    <div class="content-wrapper">
      <div class="demo-content">
        <h2 class="demo-title">Interactive Blob Animation</h2>
        <p class="demo-description">
          Move your cursor anywhere to see the blobs smoothly follow with spring physics.
          Notice how they lag behind with different speeds.
        </p>
        <div class="demo-stats">
          <div class="stat">
            <span class="stat-label">Mouse Position:</span>
            <span class="stat-value">{{ Math.round(mouseX.get()) }}, {{ Math.round(mouseY.get()) }}</span>
          </div>
          <div class="stat">
            <span class="stat-label">Blob 1:</span>
            <span class="stat-value">{{ Math.round(blob1X.get()) }}, {{ Math.round(blob1Y.get()) }}</span>
          </div>
          <div class="stat">
            <span class="stat-label">Blob 2:</span>
            <span class="stat-value">{{ Math.round(blob2X.get()) }}, {{ Math.round(blob2Y.get()) }}</span>
          </div>
        </div>

        <!-- Interactive content -->
        <div class="interactive-content">
          <button class="demo-button">Hover me!</button>
          <p class="small-text">Move your cursor around - blobs will follow smoothly</p>
        </div>
      </div>
    </div>

    <!-- Visible cursor pointer -->
    <motion.div class="cursor-pointer" :style="{
      left: mouseX,
      top: mouseY
    }" />
  </div>
</template>

<style scoped>
.demo-section {
  min-height: 100vh;
  position: relative;
  background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
  overflow: hidden;
  cursor: none;
}

.blobs-container {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 1;
}

.blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.6;
  pointer-events: none;
  will-change: transform;
}

.blob-1 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle,
      rgba(255, 0, 110, 0.8) 0%,
      rgba(131, 56, 236, 0.6) 50%,
      rgba(58, 134, 255, 0.4) 100%);
}

.blob-2 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle,
      rgba(255, 123, 0, 0.7) 0%,
      rgba(255, 0, 110, 0.5) 50%,
      rgba(131, 56, 236, 0.3) 100%);
}

.content-wrapper {
  position: relative;
  z-index: 10;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 2rem;
  pointer-events: none;
}

.demo-content {
  text-align: center;
  color: white;
  max-width: 700px;
  pointer-events: auto;
}

.demo-title {
  font-size: 3.5rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
  background: linear-gradient(45deg, #ff006e, #8338ec, #3a86ff);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  line-height: 1.2;
}

.demo-description {
  font-size: 1.3rem;
  opacity: 0.9;
  margin-bottom: 2rem;
  line-height: 1.7;
}

.demo-stats {
  display: flex;
  gap: 2rem;
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: 2rem;
  padding: 1rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  backdrop-filter: blur(10px);
}

.stat {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  min-width: 120px;
}

.stat-label {
  font-size: 0.9rem;
  opacity: 0.7;
}

.stat-value {
  font-size: 1.1rem;
  font-weight: bold;
  color: #00f5ff;
}

.interactive-content {
  margin-top: 2rem;
}

.demo-button {
  padding: 12px 24px;
  background: linear-gradient(45deg, #ff006e, #8338ec);
  color: white;
  border: none;
  border-radius: 25px;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-bottom: 1rem;
}

.demo-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(255, 0, 110, 0.3);
}

.small-text {
  font-size: 0.9rem;
  opacity: 0.7;
  margin: 0;
}

.cursor-pointer {
  position: fixed;
  width: 20px;
  height: 20px;
  background: rgba(255, 255, 255, 0.9);
  border: 2px solid rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  pointer-events: none;
  transform: translate(-50%, -50%);
  z-index: 100;
  box-shadow:
    0 0 20px rgba(255, 255, 255, 0.6),
    0 0 40px rgba(255, 255, 255, 0.3);
}

@media (max-width: 768px) {
  .demo-section {
    cursor: auto;
  }

  .demo-title {
    font-size: 2.5rem;
  }

  .demo-description {
    font-size: 1.1rem;
  }

  .demo-stats {
    flex-direction: column;
    gap: 1rem;
  }

  .blob-1 {
    width: 300px;
    height: 300px;
  }

  .blob-2 {
    width: 250px;
    height: 250px;
  }

  .cursor-pointer {
    display: none;
  }
}
</style>