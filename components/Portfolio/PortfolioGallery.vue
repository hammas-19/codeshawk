<template>
  <section class="md:py-16 pb-5 md:pb-10 px-4 sm:px-6 lg:px-8">
    <!-- Loading State -->
    <div v-if="loading" class="flex justify-center items-center py-20">
      <div class="animate-spin rounded-full h-12 w-12 border-b-2 border-blue-600"></div>
    </div>

    <!-- Error State -->
    <div v-else-if="error" class="text-center py-20">
      <p class="text-red-600 text-lg">{{ error }}</p>
      <button @click="fetchProjects" class="mt-4 px-6 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700">
        Retry
      </button>
    </div>

    <!-- Projects Grid -->
    <div v-else class="grid lg:grid-cols-2 mx-auto md:gap-10 gap-5">
      <div v-for="(project) in projects" :key="project.slug">
        <div class="w-full relative">
          <!-- Gradient Background -->
          <div class="w-full h-full absolute inset-0 md:rounded-[30px] rounded-[18px]" :style="{
            background: `linear-gradient(135deg, ${getProjectColor(project.color_code)}33, ${getProjectColor(project.color_code)}44, ${getProjectColor(project.color_code)}55)`,
          }" />

          <!-- Main Card -->
          <div
            class="border-2 md:rounded-[30px] rounded-[18px] border-black w-full bg-white hover:bg-transparent backdrop-blur-sm overflow-hidden transition-all duration-300 hover:scale-105 cursor-pointer"
            :style="{ borderColor: getProjectColor(project.color_code) }" @click="handleProjectClick(project)">

            <!-- Header Section -->
            <div class="md:py-10 py-6 md:px-8 px-4">
              <div class="flex justify-between items-center">
                <div class="flex items-center gap-6">
                  <img :src="getImageUrl(project.project_icon)" :alt="project.title"
                    class="h-12 w-12 object-cover rounded-xl" @error="handleImageError">
                  <h3 class="text-gray-900 font-bold md:text-4xl sm:text-2xl text-lg uppercase">
                    {{ project.title }}
                  </h3>
                </div>

                <!-- Arrow Button -->
                <button
                  class="group relative flex size-10 items-center justify-center gap-1 rounded-lg w-full max-w-[40px] hover:bg-gray-100 transition-colors duration-200">
                  <div class="size-1 rounded-full bg-black duration-300 group-hover:opacity-0" />
                  <div
                    class="relative size-1 origin-center rounded-full bg-black duration-300 before:absolute before:right-[2px] before:h-1 before:origin-right before:rounded-full before:bg-black before:delay-300 before:duration-300 after:absolute after:right-[2px] after:h-1 after:origin-right after:rounded-full after:bg-black after:delay-300 after:duration-300 group-hover:w-6 group-hover:before:w-3.5 group-hover:before:-rotate-45 group-hover:after:w-3.5 group-hover:after:rotate-45" />
                  <div class="size-1 rounded-full bg-black duration-300 group-hover:opacity-0" />
                </button>
              </div>
            </div>

            <!-- Folder Design -->
            <div class="flex flex-col md:rounded-[18px] rounded-[10px] overflow-hidden w-full">
              <!-- Folder Tab -->
              <div class="flex w-[45%] md:w-[30%] min-h-[40px]">
                <div class="w-3/2 min-h-full mb-[-1px] rounded-tr-sm"
                  :style="{ backgroundColor: getProjectColor(project.color_code) }" />
                <div class="theCurve w-[70px] min-h-full md:ml-[-2px] ml-[-2px] mb-[-1px]"
                  :style="{ backgroundColor: getProjectColor(project.color_code) }" />
              </div>

              <!-- Main Content Area -->
              <div
                class="md:min-h-[260px] md:rounded-tr-[18px] rounded-tr-[10px] flex flex-col justify-between md:p-6 p-4 sm:gap-8 gap-5"
                :style="{ backgroundColor: getProjectColor(project.color_code) }">
                <div class="flex-1">
                  <p class="text-white sm:text-xl text-sm line-clamp-3 leading-relaxed">
                    {{ project.short_description }}
                  </p>
                </div>

                <!-- Project Info -->
                <div class="flex flex-wrap gap-3">
                  <div class="bg-white/10 md:p-3 p-2 rounded-2xl flex justify-center items-center backdrop-blur-sm">
                    <span class="md:text-sm text-xs text-white font-medium">{{ project.category }}</span>
                  </div>
                  <div class="bg-white/10 md:p-3 p-2 rounded-2xl flex justify-center items-center backdrop-blur-sm">
                    <span class="md:text-sm text-xs text-white font-medium">{{ project.location }}</span>
                  </div>
                  <div class="bg-white/10 md:p-3 p-2 rounded-2xl flex justify-center items-center backdrop-blur-sm">
                    <span class="md:text-sm text-xs text-white font-medium">{{ formatDate(project.project_date)
                      }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// API Configuration
const API_URL = 'http://147.79.100.203/api/projects/'

// Reactive data
const projects = ref([])
const loading = ref(true)
const error = ref(null)

// Base URL for images
const BASE_URL = 'http://147.79.100.203'

// Color mapping for different color codes
const colorMap = {
  red: '#ef4444',
  blue: '#3b82f6',
  green: '#10b981',
  purple: '#8b5cf6',
  yellow: '#f59e0b',
  pink: '#ec4899',
  indigo: '#6366f1',
  gray: '#6b7280',
  orange: '#f97316',
  teal: '#14b8a6'
}

// Methods
const fetchProjects = async () => {
  try {
    loading.value = true
    error.value = null

    const response = await fetch(API_URL)
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`)
    }

    const data = await response.json()
    projects.value = data

  } catch (err) {
    error.value = `Failed to load projects: ${err.message}`
    console.error('Error fetching projects:', err)
  } finally {
    loading.value = false
  }
}

const getImageUrl = (imagePath) => {
  if (!imagePath) return 'https://via.placeholder.com/100x100?text=No+Image'
  if (imagePath.startsWith('http')) return imagePath
  return `${BASE_URL}${imagePath}`
}

const getProjectColor = (colorCode) => {
  return colorMap[colorCode?.toLowerCase()] || colorMap.blue
}

const formatDate = (dateString) => {
  if (!dateString) return ''
  const date = new Date(dateString)
  return date.toLocaleDateString('en-US', {
    year: 'numeric',
    month: 'short'
  })
}

const handleProjectClick = (project) => {
  // Emit event or handle navigation
  console.log('Project clicked:', project)
  // You can add your routing logic here
  // Example: router.push(`/projects/${project.slug}`)
}

const handleImageError = (event) => {
  event.target.src = 'https://via.placeholder.com/100x100?text=No+Image'
}

// Lifecycle
onMounted(() => {
  fetchProjects()
})

// Expose methods for parent component
defineExpose({
  fetchProjects,
  projects
})
</script>

<style scoped>
.theCurve {
  clip-path: polygon(0 0, 0 0, 100% 100%, 0% 100%);
}

.line-clamp-3 {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.animate-spin {
  animation: spin 1s linear infinite;
}
</style>