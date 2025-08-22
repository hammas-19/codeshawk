<template>
  <section class="py-16 lg:py-24 px-4 sm:px-6 lg:px-8">
    <div class="w-full mx-auto">
      <div class="grid grid-cols-1 lg:grid-cols-8 md:grid-cols-6 gap-8 items-start ">
        <!-- Left Column - Image and Badge -->
        <div class="lg:col-span-2 md:col-span-2 col-span-1 space-y-6">
          <!-- Badge -->
          <div
            class="inline-flex items-center px-4 py-2 bg-white rounded-full text-sm font-medium text-gray-600 shadow-sm">
            <span class="w-2 h-2 bg-gray-400 rounded-full mr-2"></span>
            {{ badge }}
          </div>

          <!-- Image -->
          <div class="relative ">
            <img src="/Stats/tileImage.png" class="aspect-square h-full w-full max-h-[300px] object-cover rounded-xl sm:rounded-2xl"
              alt="">
            <!-- Optional overlay for better image presentation -->
            <div class="absolute inset-0 bg-gradient-to-t from-black/10 to-transparent rounded-2xl"></div>
          </div>
        </div>

        <!-- Middle Column - Content -->
        <div class="lg:col-span-4 md:col-span-2 col-span-1 space-y-6">
          <!-- Main Heading -->
          <h2 class="text-4xl lg:text-5xl text-gray-900 leading-tight">
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
        <div class="lg:col-span-2 md:col-span-2 col-span-1 h-fit">
          <div class=" relative">
            <ThemeBtn :small="true" class="absolute bottom-0 right-0" />
            <div class=" bg-slateBlue inverted-radius flex items-end justify-center relative z-0">
              <div class="mt-5 absolute inset-0 w-full flex flex-col md:px-5 px-4">
                <span class="flex items-center gap-2 text-white">
                  ✦
                  <span class="text-xs">
                    Need Help
                  </span>
                </span>
                <span class="md:text-3xl text-lg  text-white">
                  <span class="relative z-10">
                    Free advice.
                  </span>
                  Book a callback
                </span>
              </div>
              <img src="/CTA/CTA1.png" class="max-w-[320px] h-fit max-h-[240px] px-8 mt-10 relative z-0" alt="">
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
/* Enhanced hover effects */
.hover\:-translate-y-1:hover {
  transform: translateY(-4px);
}

/* Smooth transitions */
* {
  transition-property: transform, box-shadow, background-color;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

/* Gradient animation for the CTA card */
.bg-gradient-to-br {
  background-size: 200% 200%;
  animation: gradientShift 6s ease infinite;
}

@keyframes gradientShift {

  0%,
  100% {
    background-position: 0% 50%;
  }

  50% {
    background-position: 100% 50%;
  }
}

.inverted-radius {
  --r: 10px;
  /* Adjust radius for smaller devices */
  --s: 25px;
  /* Adjust size of inner curve */
  --x: 80px;
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
</style>
