<template>
  <section class="bg-gray-50 py-16 lg:py-24 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12 items-start">
        <!-- Left Column - Image and Badge -->
        <div class="lg:col-span-5 space-y-6">
          <!-- Badge -->
          <div
            class="inline-flex items-center px-4 py-2 bg-white rounded-full text-sm font-medium text-gray-600 shadow-sm">
            <span class="w-2 h-2 bg-gray-400 rounded-full mr-2"></span>
            {{ badge }}
          </div>

          <!-- Image -->
          <div class="relative">
            <img :src="image" :alt="imageAlt" class="w-full h-96 lg:h-[500px] object-cover rounded-2xl shadow-lg">
            <!-- Optional overlay for better image presentation -->
            <div class="absolute inset-0 bg-gradient-to-t from-black/10 to-transparent rounded-2xl"></div>
          </div>
        </div>

        <!-- Middle Column - Content -->
        <div class="lg:col-span-4 space-y-6">
          <!-- Main Heading -->
          <h2 class="text-4xl lg:text-5xl font-bold text-gray-900 leading-tight">
            {{ title }}
          </h2>

          <!-- Content Paragraphs -->
          <div class="space-y-6 text-gray-700 leading-relaxed">
            <p class="text-lg">
              {{ introText }}
            </p>

            <p>
              We're more than just a tech company; we're a collective of
              <span class="font-semibold text-gray-900">{{ teamDescription.roles }}</span>
              {{ teamDescription.description }}
              <span class="font-semibold text-gray-900">{{ services.join(', ') }}</span>.
              {{ servicesDescription }}
            </p>

            <p>
              {{ approachText }}
              <span class="font-semibold text-gray-900">{{ coreValues.join(', ') }}</span>
              {{ closingText }}
            </p>
          </div>
        </div>

        <!-- Right Column - CTA Card -->
        <div class="lg:col-span-3">
          <div
            class="bg-gradient-to-br from-blue-500 to-indigo-600 rounded-2xl p-6 lg:p-8 text-white relative overflow-hidden">
            <!-- Background Pattern -->
            <div class="absolute top-0 right-0 w-32 h-32 bg-white/10 rounded-full -translate-y-16 translate-x-16"></div>
            <div class="absolute bottom-0 left-0 w-24 h-24 bg-white/5 rounded-full translate-y-12 -translate-x-12">
            </div>

            <!-- Content -->
            <div class="relative z-10">
              <!-- CTA Badge -->
              <div class="inline-flex items-center px-3 py-1 bg-white/20 rounded-full text-sm font-medium mb-4">
                <span class="w-2 h-2 bg-white rounded-full mr-2"></span>
                {{ ctaCard.badge }}
              </div>

              <!-- CTA Title -->
              <h3 class="text-2xl lg:text-3xl font-bold mb-4 leading-tight">
                {{ ctaCard.title }}
              </h3>

              <!-- CTA Image/Illustration -->
              <div class="mb-6">
                <img :src="ctaCard.image" :alt="ctaCard.imageAlt" class="w-full h-32 object-contain">
              </div>

              <!-- CTA Button -->
              <button @click="handleCtaClick"
                class="flex items-center justify-between w-full bg-white/20 hover:bg-white/30 rounded-lg px-4 py-3 transition-all duration-200 group">
                <span class="font-medium">{{ ctaCard.buttonText }}</span>
                <div
                  class="w-8 h-8 bg-white/20 rounded-full flex items-center justify-center group-hover:bg-white/30 transition-colors">
                  <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                      d="M17 8l4 4m0 0l-4 4m4-4H3" />
                  </svg>
                </div>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Define props with defaults
const props = defineProps({
  // Badge
  badge: {
    type: String,
    default: 'Who We Are'
  },

  // Main content
  title: {
    type: String,
    default: 'The Codes Hawk Story'
  },

  // Image
  image: {
    type: String,
    default: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80'
  },

  imageAlt: {
    type: String,
    default: 'Professional working on laptop'
  },

  // Content text
  introText: {
    type: String,
    default: 'At Codes Hawk, we believe in the transformative power of technology. Founded on the principle of delivering exceptional digital services, our journey began with a clear vision: to empower businesses and individuals to thrive in the digital age.'
  },

  teamDescription: {
    type: Object,
    default: () => ({
      roles: 'designers, developers, strategists, and problem-solvers',
      description: ' who are deeply committed to innovation and client success. Our diverse expertise encompasses '
    })
  },

  services: {
    type: Array,
    default: () => [
      'web design',
      'web development',
      'UI/UX design',
      'automation',
      'AI integration',
      'database management',
      'SEO',
      'digital marketing',
      'and content creation'
    ]
  },

  servicesDescription: {
    type: String,
    default: ' This breadth allows us to offer comprehensive, end-to-end solutions that are both effective and forward-thinking.'
  },

  approachText: {
    type: String,
    default: 'Our approach is collaborative. We listen to your challenges, understand your aspirations, and then meticulously craft solutions that not only meet your immediate needs but also position you for long-term success. We pride ourselves on '
  },

  coreValues: {
    type: Array,
    default: () => [
      'transparency',
      'clear communication',
      'and a relentless pursuit of excellence'
    ]
  },

  closingText: {
    type: String,
    default: ' in every project we undertake.'
  },

  // CTA Card
  ctaCard: {
    type: Object,
    default: () => ({
      badge: 'Just starting out?',
      title: 'Download a company brochure',
      image: 'https://images.unsplash.com/photo-1460925895917-afdab827c52f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80',
      imageAlt: 'Laptop with business presentation',
      buttonText: 'Get A Copy'
    })
  }
})

// Emit events for parent component
const emit = defineEmits(['cta-clicked'])

// Methods
const handleCtaClick = () => {
  emit('cta-clicked', {
    action: 'download-brochure',
    timestamp: new Date().toISOString()
  })
}
</script>

<style scoped>
/* Custom scrollbar for text content if needed */
.content-scroll {
  scrollbar-width: thin;
  scrollbar-color: rgba(156, 163, 175, 0.5) transparent;
}

.content-scroll::-webkit-scrollbar {
  width: 4px;
}

.content-scroll::-webkit-scrollbar-track {
  background: transparent;
}

.content-scroll::-webkit-scrollbar-thumb {
  background-color: rgba(156, 163, 175, 0.5);
  border-radius: 2px;
}

/* Ensure text styling is consistent */
.text-content p {
  line-height: 1.75;
}

/* Hover effects for interactive elements */
.cta-card {
  transition: transform 0.2s ease;
}

.cta-card:hover {
  transform: translateY(-2px);
}
</style>