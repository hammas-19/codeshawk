<template>
  <section class="bg-gray-50 py-16 lg:py-24 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <!-- Header Section -->
      <div class="text-center mb-16">
        <!-- Badge -->
        <div
          class="inline-flex items-center px-4 py-2 bg-white rounded-full text-sm font-medium text-gray-600 mb-6 shadow-sm">
          <span class="w-2 h-2 bg-gray-400 rounded-full mr-2"></span>
          Our expert crew
        </div>

        <!-- Main Heading -->
        <div class="mb-6">
          <h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold text-gray-900 leading-tight">
            Meet the<br>
            leadership team
          </h2>
        </div>

        <!-- Description -->
        <p class="text-gray-600 text-lg max-w-md mx-auto">
          We are all passionate and committed to deliver high quality services to our clients.
        </p>
      </div>

      <!-- Team Slider -->
      <div class="relative">
        <!-- Slider Container -->
        <div ref="slider" class="keen-slider" @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave">
          <!-- Team Member Card -->
          <div v-for="member in teamMembers" :key="member.id" class="keen-slider__slide">
            <div
              class="group relative bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 hover:-translate-y-2 cursor-pointer h-full"
              @click="handleTeamMemberClick(member)">
              <div class="aspect-[3/4] relative overflow-hidden bg-gradient-to-br" :class="member.gradient">
                <img :src="member.image" :alt="member.name"
                  class="w-full h-full object-cover transition-transform duration-300 group-hover:scale-105"
                  loading="lazy">
                <!-- Hover Overlay -->
                <div class="absolute inset-0 bg-black/0 group-hover:bg-black/10 transition-colors duration-300"></div>

                <!-- Plus Icon -->
                <button
                  class="absolute bottom-4 right-4 w-10 h-10 bg-white rounded-full flex items-center justify-center shadow-lg opacity-0 group-hover:opacity-100 transition-all duration-300 hover:scale-110"
                  @click.stop="handleViewProfile(member)" :aria-label="`View ${member.name}'s profile`">
                  <svg class="w-5 h-5 text-gray-800" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
                  </svg>
                </button>
              </div>

              <!-- Content -->
              <div class="p-6">
                <h3 class="text-xl font-bold text-gray-900 mb-1">{{ member.name }}</h3>
                <p class="text-gray-600 text-sm">{{ member.position }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Navigation Arrows -->
        <!-- <button v-if="slider" @click="slider.prev()"
          class="absolute left-4 top-1/2 -translate-y-1/2 w-12 h-12 bg-white rounded-full shadow-lg flex items-center justify-center hover:bg-gray-50 transition-colors duration-200 z-10"
          :class="{ 'opacity-50 cursor-not-allowed': currentSlide === 0 }">
          <svg class="w-6 h-6 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>

        <button v-if="slider" @click="slider.next()"
          class="absolute right-4 top-1/2 -translate-y-1/2 w-12 h-12 bg-white rounded-full shadow-lg flex items-center justify-center hover:bg-gray-50 transition-colors duration-200 z-10"
          :class="{ 'opacity-50 cursor-not-allowed': currentSlide >= maxSlide }">
          <svg class="w-6 h-6 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button> -->
      </div>

      <!-- Slider Dots -->
      <!-- <div v-if="slider" class="flex justify-center mt-8 space-x-2">
        <button v-for="(dot, idx) in dots" :key="idx" @click="slider.moveToIdx(idx)"
          class="w-3 h-3 rounded-full transition-colors duration-200"
          :class="idx === currentSlide ? 'bg-blue-600' : 'bg-gray-300 hover:bg-gray-400'" />
      </div> -->
    </div>
  </section>
</template>

<script setup>
// Team data - can be moved to composables/useTeam.js or stores/team.js
const teamMembers = ref([
  {
    id: 1,
    name: 'Marvin Jones',
    position: 'Ceo - Founder',
    image: 'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80',
    gradient: 'from-purple-100 to-blue-100',
    bio: 'Visionary leader with 15+ years in tech innovation.',
    social: {
      linkedin: 'https://linkedin.com/in/marvinjones',
      twitter: 'https://twitter.com/marvinjones'
    }
  },
  {
    id: 2,
    name: 'Arlene Bell',
    position: 'Chief Marketing',
    image: 'https://images.unsplash.com/photo-1494790108755-2616b612b4c3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80',
    gradient: 'from-orange-100 to-yellow-100',
    bio: 'Marketing strategist with expertise in digital transformation.',
    social: {
      linkedin: 'https://linkedin.com/in/arlenebell',
      twitter: 'https://twitter.com/arlenebell'
    }
  },
  {
    id: 3,
    name: 'Guy Hawkins',
    position: 'Executive Admin',
    image: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80',
    gradient: 'from-green-100 to-blue-100',
    bio: 'Operations expert ensuring seamless business processes.',
    social: {
      linkedin: 'https://linkedin.com/in/guyhawkins'
    }
  },
  {
    id: 4,
    name: 'Cody Fisher',
    position: 'Office Manager',
    image: 'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80',
    gradient: 'from-pink-100 to-purple-100',
    bio: 'Office management specialist fostering productive work environments.',
    social: {
      linkedin: 'https://linkedin.com/in/codyfisher'
    }
  },
  {
    id: 5,
    name: 'Sarah Johnson',
    position: 'Lead Developer',
    image: 'https://images.unsplash.com/photo-1517841905240-472988babdf9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80',
    gradient: 'from-cyan-100 to-blue-100',
    bio: 'Full-stack developer with expertise in modern web technologies.',
    social: {
      linkedin: 'https://linkedin.com/in/sarahjohnson',
      github: 'https://github.com/sarahjohnson'
    }
  },
  {
    id: 6,
    name: 'Michael Chen',
    position: 'UX Designer',
    image: 'https://images.unsplash.com/photo-1519345182560-3f2917c472ef?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80',
    gradient: 'from-indigo-100 to-purple-100',
    bio: 'Creative designer focused on user-centered design solutions.',
    social: {
      linkedin: 'https://linkedin.com/in/michaelchen',
      dribbble: 'https://dribbble.com/michaelchen'
    }
  }
])

// Slider state
const currentSlide = ref(0)

// Initialize slider using correct nuxt-keen-slider syntax
const [slider] = useKeenSlider({
  loop: true,
  mode: "free",
  slides: {
    perView: 1,
    spacing: 15,
  },
  breakpoints: {
    "(min-width: 640px)": {
      slides: {
        perView: 2,
        spacing: 15,
      },
    },
    "(min-width: 1024px)": {
      slides: {
        perView: 3,
        spacing: 20,
      },
    },
    "(min-width: 1280px)": {
      slides: {
        perView: 4,
        spacing: 20,
      },
    },
  },
  slideChanged: (s) => {
    if (s && s.track && s.track.details) {
      currentSlide.value = s.track.details.rel
    }
  },
})

// Computed properties
const maxSlide = computed(() => {
  if (!slider.value || !slider.value.track || !slider.value.track.details) return 0
  return slider.value.track.details.slides.length - 1
})

const dots = computed(() => {
  if (!slider.value || !slider.value.track || !slider.value.track.details) return []
  return Array.from({ length: slider.value.track.details.slides.length }, (_, i) => i)
})

// Methods
const handleTeamMemberClick = (member) => {
  // Navigate to detailed profile page
  navigateTo(`/team/${member.id}`)
}

const handleViewProfile = (member) => {
  // Open modal with detailed info or external profile
  console.log('Opening profile for:', member.name)
  // Could trigger a modal, navigation, or API call
}

// Auto-play functionality (optional)
const autoPlay = ref(true)
let autoPlayInterval = null

const startAutoPlay = () => {
  if (autoPlay.value && slider.value) {
    autoPlayInterval = setInterval(() => {
      slider.value.next()
    }, 4000)
  }
}

const stopAutoPlay = () => {
  if (autoPlayInterval) {
    clearInterval(autoPlayInterval)
    autoPlayInterval = null
  }
}

// Pause auto-play on hover
const handleMouseEnter = () => {
  stopAutoPlay()
}

const handleMouseLeave = () => {
  startAutoPlay()
}

// Lifecycle
onMounted(() => {
  nextTick(() => {
    if (autoPlay.value) {
      startAutoPlay()
    }
  })
})

onUnmounted(() => {
  stopAutoPlay()
})
</script>

<style scoped>
/* Additional custom styles if needed */
.aspect-\[3\/4\] {
  aspect-ratio: 3/4;
}
</style>