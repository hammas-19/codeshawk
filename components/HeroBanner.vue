<template>
  <section
    class="relative h-80 sm:h-96 lg:h-[600px] rounded-2xl sm:rounded-3xl overflow-hidden mx-2 my-8"
    :style="{ backgroundImage: `url(${backgroundImage})` }">
    <!-- Background Image with Overlay -->
    <div class="absolute inset-0 bg-black/60"></div>

    <!-- Content Container -->
    <div class="relative z-10 h-full flex flex-col justify-between p-6 sm:p-8 lg:p-12">
      <!-- Breadcrumb Navigation -->
      <nav class="flex items-center space-x-3 text-white text-sm w-fit px-5 py-3 rounded-xl bg-[#bbbaba35] backdrop-blur-md">
        <NuxtLink v-for="(crumb, index) in breadcrumbs" :key="index" :to="crumb.href"
          class="hover:text-[#7af1c7] transition-colors duration-200 "
          :class="{ 'text-white': index === breadcrumbs.length - 1 }">
          {{ crumb.label }}
        </NuxtLink>
        <span v-if="index < breadcrumbs.length - 1" v-for="(crumb, index) in breadcrumbs.slice(0, -1)"
          :key="`separator-${index}`" class="text-white">
          •
        </span>
      </nav>

      <!-- Hero Content -->
      <div class="flex-1 flex flex-col justify-center">
        <div class="max-w-4xl">
          <!-- Main Title -->
          <h1 class="text-4xl sm:text-5xl lg:text-6xl xl:text-7xl font-medium text-white leading-tight mb-4 sm:mb-6">
            {{ title }}
          </h1>

          <!-- Subtitle -->
          <p v-if="subtitle" class="text-lg sm:text-xl lg:text-2xl text-white font-light max-w-2xl">
            {{ subtitle }}
          </p>

          <!-- Description -->
          <p v-if="description" class="text-base sm:text-lg text-white mt-4 max-w-2xl leading-relaxed">
            {{ description }}
          </p>

          <!-- Call to Action Button (Optional) -->
          <div v-if="showCta" class="mt-8">
            <NuxtLink :to="ctaLink"
              class="inline-flex items-center px-6 py-3 bg-white text-gray-900 rounded-lg hover:bg-gray-100 transition-all duration-200 hover:scale-105 font-medium">
              {{ ctaText }}
              <svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>

    <!-- Optional Scroll Indicator -->
    <div v-if="showScrollIndicator" class="absolute bottom-6 left-1/2 transform -translate-x-1/2 animate-bounce">
      <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
      </svg>
    </div>
  </section>
</template>

<script setup>
// Define props with defaults
const props = defineProps({
  // Background image
  backgroundImage: {
    type: String,
    default: 'https://images.unsplash.com/photo-1521737604893-d14cc237f11d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2084&q=80'
  },

  // Main title
  title: {
    type: String,
    default: 'We are CodesHawk'
  },

  // Subtitle
  subtitle: {
    type: String,
    default: 'Passionate Innovators, Your Digital Partners.'
  },

  // Optional description
  description: {
    type: String,
    default: ''
  },

  // Breadcrumb navigation
  breadcrumbs: {
    type: Array,
    default: () => [
      { label: 'Home', href: '/' },
      { label: 'About Us', href: '/about' }
    ]
  },

  // Call to action
  showCta: {
    type: Boolean,
    default: false
  },

  ctaText: {
    type: String,
    default: 'Get Started'
  },

  ctaLink: {
    type: String,
    default: '/contact'
  },

  // Additional options
  showScrollIndicator: {
    type: Boolean,
    default: false
  },

  // Height variants
  height: {
    type: String,
    default: 'default', // default, small, large, full
    validator: (value) => ['small', 'default', 'large', 'full'].includes(value)
  }
})

// Computed height classes
const heightClasses = computed(() => {
  switch (props.height) {
    case 'small':
      return 'h-64 sm:h-80 lg:h-96'
    case 'large':
      return 'h-96 sm:h-[500px] lg:h-[600px]'
    case 'full':
      return 'h-screen'
    default:
      return 'h-80 sm:h-96 lg:h-[500px]'
  }
})
</script>

<style scoped>
/* Ensure background image covers properly */
section {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

/* Smooth hover transitions */
nav a {
  position: relative;
}

nav a::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 1px;
  background-color: white;
  transition: width 0.3s ease;
}

nav a:hover::after {
  width: 100%;
}
</style>