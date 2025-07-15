<template>
  <section class="py-16 md:py-24">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="flex justify-between items-center mb-12">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-900">
          Key Differentiators
        </h2>
        <button
          class="hidden md:flex items-center space-x-2 px-6 py-3 bg-blue-600 text-white rounded-full hover:bg-blue-700 transition-all duration-200 hover:scale-105">
          <span class="font-medium">Learn More About Our Story</span>
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
          </svg>
        </button>
      </div>

      <!-- Cards Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        <!-- Card 1: Tailored Solutions -->
        <div class="bg-gray-50 rounded-2xl p-8 hover:shadow-lg transition-all duration-300 hover:-translate-y-1">
          <div class="flex justify-center mb-6">
            <div class="w-16 h-16 bg-white rounded-2xl flex items-center justify-center text-3xl shadow-sm">
              💡
            </div>
          </div>
          <h3 class="text-2xl font-bold text-gray-900 mb-4">
            Tailored Solutions
          </h3>
          <p class="text-gray-600 leading-relaxed">
            Every business is unique. We listen intently to your challenges and craft custom strategies, ensuring our
            solutions perfectly fit your specific needs and drive tangible results.
          </p>
        </div>

        <!-- Card 2: Expert Team -->
        <div class="bg-gray-50 rounded-2xl p-8 hover:shadow-lg transition-all duration-300 hover:-translate-y-1">
          <div class="flex justify-center mb-6">
            <div class="w-16 h-16 bg-white rounded-2xl flex items-center justify-center text-3xl shadow-sm">
              👥
            </div>
          </div>
          <h3 class="text-2xl font-bold text-gray-900 mb-4">
            Expert Team
          </h3>
          <p class="text-gray-600 leading-relaxed">
            Our diverse team comprises seasoned web developers, UI/UX designers, AI specialists, digital marketers, and
            content strategists, all united by a passion for technology and a commitment to excellence.
          </p>
        </div>

        <!-- Card 3: Results-Driven Approach -->
        <div class="bg-gray-50 rounded-2xl p-8 hover:shadow-lg transition-all duration-300 hover:-translate-y-1">
          <div class="flex justify-center mb-6">
            <div class="w-16 h-16 bg-white rounded-2xl flex items-center justify-center text-3xl shadow-sm">
              📈
            </div>
          </div>
          <h3 class="text-2xl font-bold text-gray-900 mb-4">
            Results-Driven Approach
          </h3>
          <p class="text-gray-600 leading-relaxed">
            Your success is our ultimate measure. We focus on delivering solutions that not only look great but also
            perform exceptionally, contributing directly to your growth and ROI.
          </p>
        </div>

        <!-- Card 4: Free Advice -->
        <div
          class="bg-gradient-to-br from-blue-500 to-purple-600 rounded-2xl p-8 text-white relative overflow-hidden hover:shadow-lg transition-all duration-300 hover:-translate-y-1">
          <div class="relative z-10">
            <div class="flex items-center space-x-2 mb-4">
              <div class="w-2 h-2 bg-white rounded-full"></div>
              <span class="text-sm font-medium opacity-90">Need help</span>
            </div>
            <h3 class="text-2xl font-bold mb-6">
              Free advice.<br>
              Book a callback
            </h3>
            <button
              class="flex items-center space-x-2 bg-white text-blue-600 px-6 py-3 rounded-full font-medium hover:bg-gray-50 transition-all duration-200 hover:scale-105">
              <span>Let's Talk</span>
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </button>
          </div>
          <!-- Background Image -->
          <div class="absolute right-0 bottom-0 w-32 h-32 opacity-20">
            <img src="https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?w=200&h=200&fit=crop&crop=face"
              alt="Customer support representative" class="w-full h-full object-cover rounded-full" />
          </div>
          <!-- Decorative elements -->
          <div class="absolute top-4 right-4 w-24 h-24 bg-white/10 rounded-full"></div>
          <div class="absolute -top-2 -right-2 w-16 h-16 bg-white/5 rounded-full"></div>
        </div>
      </div>

      <!-- Mobile CTA -->
      <div class="md:hidden mt-8 text-center">
        <button
          class="flex items-center space-x-2 px-6 py-3 bg-blue-600 text-white rounded-full hover:bg-blue-700 transition-all duration-200 hover:scale-105 mx-auto">
          <span class="font-medium">Learn More About Our Story</span>
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
          </svg>
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
// No reactive state needed for this static section
</script>

<style scoped>
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
</style>