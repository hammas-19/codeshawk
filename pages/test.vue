<template>
  <div>
    <!-- Global blobs that change color based on active section -->
    <GlobalAnimatedBlobs :active-section="activeSection" />

    <!-- Section 1: Red and Black theme -->
    <section ref="section1" class="example-section section-1" data-section="section1">
      <div class="content">
        <h1 class="title red-theme">Section 1</h1>
        <p class="description">Red and black blobs following your cursor</p>
        <button class="btn red-btn">Explore</button>
      </div>
    </section>

    <!-- Section 2: Blue and Yellow theme -->
    <section ref="section2" class="example-section section-2" data-section="section2">
      <div class="content">
        <h1 class="title blue-theme">Section 2</h1>
        <p class="description">Blue and yellow blobs with same cursor tracking</p>
        <button class="btn blue-btn">Discover</button>
      </div>
    </section>

    <!-- Section 3: Purple and Pink theme -->
    <section ref="section3" class="example-section section-3" data-section="section3">
      <div class="content">
        <h1 class="title purple-theme">Section 3</h1>
        <p class="description">Purple and pink blobs - continuous movement</p>
        <div class="card">
          <h3>Interactive Card</h3>
          <p>Scroll between sections and watch the blobs change colors smoothly</p>
          <button class="card-btn">Try it!</button>
        </div>
      </div>
    </section>

    <!-- Section 4: Green and Teal theme -->
    <section ref="section4" class="example-section section-4" data-section="section4">
      <div class="content">
        <h1 class="title green-theme">Section 4</h1>
        <p class="description">Green and teal blobs - one continuous experience</p>
        <div class="stats">
          <div class="stat-item">
            <span class="stat-number">01</span>
            <span class="stat-label">Smooth Transitions</span>
          </div>
          <div class="stat-item">
            <span class="stat-number">02</span>
            <span class="stat-label">Global Cursor Tracking</span>
          </div>
          <div class="stat-item">
            <span class="stat-number">03</span>
            <span class="stat-label">Dynamic Colors</span>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const activeSection = ref('section1')

// Section refs
const section1 = ref()
const section2 = ref()
const section3 = ref()
const section4 = ref()

let observer

onMounted(() => {
  // Create intersection observer to detect which section is active
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting && entry.intersectionRatio > 0.5) {
          const sectionName = entry.target.dataset.section
          if (sectionName) {
            activeSection.value = sectionName
          }
        }
      })
    },
    {
      threshold: [0.5] // Trigger when 50% of section is visible
    }
  )

  // Observe all sections
  const sections = [section1.value, section2.value, section3.value, section4.value]
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
.example-section {
  height: 100vh;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10;
}


.content {
  text-align: center;
  padding: 2rem;
  max-width: 700px;
  position: relative;
  z-index: 20;
}

.title {
  font-size: 3.5rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
  line-height: 1.2;
}

.red-theme {
  color: #cdf68b;
  text-shadow: 0 0 20px rgba(255, 68, 68, 0.5);
}

.blue-theme {
  color: #4488ff;
  text-shadow: 0 0 20px rgba(68, 136, 255, 0.5);
}

.purple-theme {
  color: #aa44ff;
  text-shadow: 0 0 20px rgba(170, 68, 255, 0.5);
}

.green-theme {
  color: #44ff88;
  text-shadow: 0 0 20px rgba(68, 255, 136, 0.5);
}

.description {
  font-size: 1.3rem;
  margin-bottom: 2rem;
  opacity: 0.9;
  color: white;
  line-height: 1.6;
}

.btn {
  padding: 15px 30px;
  border: none;
  border-radius: 30px;
  font-size: 1.1rem;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.red-btn {
  background: linear-gradient(45deg, #ff4444, #cc0000);
  color: white;
}

.red-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 30px rgba(255, 68, 68, 0.4);
}

.blue-btn {
  background: linear-gradient(45deg, #4488ff, #0044cc);
  color: white;
}

.blue-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 30px rgba(68, 136, 255, 0.4);
}

.card {
  background: rgba(255, 255, 255, 0.1);
  padding: 2rem;
  border-radius: 16px;
  backdrop-filter: blur(15px);
  margin-top: 1rem;
  color: white;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.card h3 {
  margin-bottom: 1rem;
  color: #aa44ff;
  font-size: 1.4rem;
}

.card-btn {
  padding: 10px 20px;
  background: linear-gradient(45deg, #aa44ff, #8800cc);
  color: white;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  margin-top: 1rem;
  transition: all 0.3s ease;
}

.card-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(170, 68, 255, 0.3);
}

.stats {
  display: flex;
  gap: 2rem;
  justify-content: center;
  flex-wrap: wrap;
  margin-top: 2rem;
}

.stat-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.stat-number {
  font-size: 2rem;
  font-weight: bold;
  color: #44ff88;
  text-shadow: 0 0 10px rgba(68, 255, 136, 0.5);
}

.stat-label {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.8);
  text-align: center;
}

@media (max-width: 768px) {
  .title {
    font-size: 2.5rem;
  }

  .description {
    font-size: 1.1rem;
  }

  .stats {
    flex-direction: column;
    gap: 1rem;
  }

  .content {
    padding: 1rem;
  }
}
</style>