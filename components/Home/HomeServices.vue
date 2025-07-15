<template>
  <section class="bg-cobalt py-20 px-4 sm:px-6 lg:px-8 mx-2 md:rounded-4xl rounded-2xl">
    <div class="max-w-7xl mx-auto">
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <!-- Left side - Image and header -->
        <div class="order-2 lg:order-1">
          <div class="relative">
            <img
              src="https://images.unsplash.com/photo-1522071820081-009f0129c71c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80"
              alt="Team collaboration" class="w-full h-96 object-cover rounded-2xl shadow-2xl" />
            <div class="absolute inset-0 bg-gradient-to-t from-black/20 to-transparent rounded-2xl"></div>

            <!-- Floating element -->
            <div class="absolute bottom-4 left-4 bg-blue-500 text-white p-3 rounded-full shadow-lg">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z">
                </path>
              </svg>
            </div>
          </div>

          <div class="mt-8">
            <div
              class="inline-flex items-center px-4 py-2 bg-blue-500/20 text-blue-300 rounded-full text-sm font-medium mb-6">
              <span class="w-2 h-2 bg-blue-400 rounded-full mr-2"></span>
              Our core services
            </div>

            <h2 class="text-4xl lg:text-5xl font-bold text-white mb-4 leading-tight">
              Comprehensive Solutions
              <br>
              <span class="text-blue-400">for the Digital Age.</span>
            </h2>
          </div>
        </div>

        <!-- Right side - Services Accordions -->
        <div class="order-1 lg:order-2 space-y-4">
          <!-- UI/UX Design - Expanded by default -->
          <div class="bg-white/10 backdrop-blur-sm rounded-xl border border-white/20 overflow-hidden">
            <button @click="toggleAccordion(0)"
              class="w-full px-6 py-6 text-left flex items-center justify-between hover:bg-white/5 transition-colors">
              <div>
                <h3 class="text-xl font-semibold text-white mb-2">UI/UX Design</h3>
                <p class="text-blue-300 text-sm">Designing Intuitive Journeys. Elevating User Satisfaction.</p>
              </div>
              <div class="flex items-center">
                <svg :class="{ 'rotate-45': activeAccordion === 0 }"
                  class="w-6 h-6 text-white transition-transform duration-300" fill="none" stroke="currentColor"
                  viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6">
                  </path>
                </svg>
              </div>
            </button>

            <div v-show="activeAccordion === 0" class="px-6 pb-6">
              <div class="border-t border-white/20 pt-4">
                <p class="text-gray-300 mb-4">
                  A beautiful interface is just the beginning. Our UI/UX design philosophy centers on creating truly
                  user-centric experiences that are not only visually appealing but also incredibly intuitive and
                  efficient.
                </p>
                <div class="flex flex-wrap gap-2">
                  <span class="px-3 py-1 bg-blue-500/20 text-blue-300 rounded-full text-sm border border-blue-500/30">
                    Banner Design
                  </span>
                  <span class="px-3 py-1 bg-blue-500/20 text-blue-300 rounded-full text-sm border border-blue-500/30">
                    Graphic Design
                  </span>
                  <span class="px-3 py-1 bg-blue-500/20 text-blue-300 rounded-full text-sm border border-blue-500/30">
                    Logo Design
                  </span>
                </div>
              </div>
            </div>
          </div>

          <!-- Database Management -->
          <div class="bg-white/10 backdrop-blur-sm rounded-xl border border-white/20 overflow-hidden">
            <button @click="toggleAccordion(1)"
              class="w-full px-6 py-6 text-left flex items-center justify-between hover:bg-white/5 transition-colors">
              <div>
                <h3 class="text-xl font-semibold text-white mb-2">Database Management & Solutions</h3>
                <p class="text-blue-300 text-sm">Secure, scalable, and optimized data infrastructure.</p>
              </div>
              <div class="flex items-center">
                <svg :class="{ 'rotate-45': activeAccordion === 1 }"
                  class="w-6 h-6 text-white transition-transform duration-300" fill="none" stroke="currentColor"
                  viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6">
                  </path>
                </svg>
              </div>
            </button>

            <div v-show="activeAccordion === 1" class="px-6 pb-6">
              <div class="border-t border-white/20 pt-4">
                <p class="text-gray-300 mb-4">
                  From database design to performance optimization, we provide comprehensive solutions that ensure your
                  data
                  is secure, accessible, and drives meaningful business insights.
                </p>
                <div class="flex flex-wrap gap-2">
                  <span
                    class="px-3 py-1 bg-green-500/20 text-green-300 rounded-full text-sm border border-green-500/30">
                    SQL Optimization
                  </span>
                  <span
                    class="px-3 py-1 bg-green-500/20 text-green-300 rounded-full text-sm border border-green-500/30">
                    Cloud Migration
                  </span>
                  <span
                    class="px-3 py-1 bg-green-500/20 text-green-300 rounded-full text-sm border border-green-500/30">
                    Data Analytics
                  </span>
                </div>
              </div>
            </div>
          </div>

          <!-- Digital Marketing -->
          <div class="bg-white/10 backdrop-blur-sm rounded-xl border border-white/20 overflow-hidden">
            <button @click="toggleAccordion(2)"
              class="w-full px-6 py-6 text-left flex items-center justify-between hover:bg-white/5 transition-colors">
              <div>
                <h3 class="text-xl font-semibold text-white mb-2">Digital Marketing</h3>
                <p class="text-blue-300 text-sm">Strategic campaigns that drive growth and engagement.</p>
              </div>
              <div class="flex items-center">
                <svg :class="{ 'rotate-45': activeAccordion === 2 }"
                  class="w-6 h-6 text-white transition-transform duration-300" fill="none" stroke="currentColor"
                  viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6">
                  </path>
                </svg>
              </div>
            </button>

            <div v-show="activeAccordion === 2" class="px-6 pb-6">
              <div class="border-t border-white/20 pt-4">
                <p class="text-gray-300 mb-4">
                  Transform your digital presence with data-driven marketing strategies that connect with your audience
                  and deliver measurable results across all channels.
                </p>
                <div class="flex flex-wrap gap-2">
                  <span
                    class="px-3 py-1 bg-purple-500/20 text-purple-300 rounded-full text-sm border border-purple-500/30">
                    SEO/SEM
                  </span>
                  <span
                    class="px-3 py-1 bg-purple-500/20 text-purple-300 rounded-full text-sm border border-purple-500/30">
                    Social Media
                  </span>
                  <span
                    class="px-3 py-1 bg-purple-500/20 text-purple-300 rounded-full text-sm border border-purple-500/30">
                    Content Strategy
                  </span>
                </div>
              </div>
            </div>
          </div>

          <!-- Content Writing -->
          <div class="bg-white/10 backdrop-blur-sm rounded-xl border border-white/20 overflow-hidden">
            <button @click="toggleAccordion(3)"
              class="w-full px-6 py-6 text-left flex items-center justify-between hover:bg-white/5 transition-colors">
              <div>
                <h3 class="text-xl font-semibold text-white mb-2">Content Writing</h3>
                <p class="text-blue-300 text-sm">Compelling narratives that engage and convert.</p>
              </div>
              <div class="flex items-center">
                <svg :class="{ 'rotate-45': activeAccordion === 3 }"
                  class="w-6 h-6 text-white transition-transform duration-300" fill="none" stroke="currentColor"
                  viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6">
                  </path>
                </svg>
              </div>
            </button>

            <div v-show="activeAccordion === 3" class="px-6 pb-6">
              <div class="border-t border-white/20 pt-4">
                <p class="text-gray-300 mb-4">
                  From blog posts to technical documentation, we craft content that speaks to your audience,
                  builds authority, and drives action across all digital touchpoints.
                </p>
                <div class="flex flex-wrap gap-2">
                  <span
                    class="px-3 py-1 bg-orange-500/20 text-orange-300 rounded-full text-sm border border-orange-500/30">
                    Blog Writing
                  </span>
                  <span
                    class="px-3 py-1 bg-orange-500/20 text-orange-300 rounded-full text-sm border border-orange-500/30">
                    Copywriting
                  </span>
                  <span
                    class="px-3 py-1 bg-orange-500/20 text-orange-300 rounded-full text-sm border border-orange-500/30">
                    Technical Docs
                  </span>
                </div>
              </div>
            </div>
          </div>

          <!-- Custom HRM/CRM Solutions -->
          <div class="bg-white/10 backdrop-blur-sm rounded-xl border border-white/20 overflow-hidden">
            <button @click="toggleAccordion(4)"
              class="w-full px-6 py-6 text-left flex items-center justify-between hover:bg-white/5 transition-colors">
              <div>
                <h3 class="text-xl font-semibold text-white mb-2">Custom HRM / CRM Solutions</h3>
                <p class="text-blue-300 text-sm">Tailored systems for streamlined business operations.</p>
              </div>
              <div class="flex items-center">
                <svg :class="{ 'rotate-45': activeAccordion === 4 }"
                  class="w-6 h-6 text-white transition-transform duration-300" fill="none" stroke="currentColor"
                  viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6">
                  </path>
                </svg>
              </div>
            </button>

            <div v-show="activeAccordion === 4" class="px-6 pb-6">
              <div class="border-t border-white/20 pt-4">
                <p class="text-gray-300 mb-4">
                  Custom-built solutions that adapt to your unique business processes, helping you manage relationships
                  and human resources more effectively than off-the-shelf alternatives.
                </p>
                <div class="flex flex-wrap gap-2">
                  <span class="px-3 py-1 bg-cyan-500/20 text-cyan-300 rounded-full text-sm border border-cyan-500/30">
                    Custom Development
                  </span>
                  <span class="px-3 py-1 bg-cyan-500/20 text-cyan-300 rounded-full text-sm border border-cyan-500/30">
                    API Integration
                  </span>
                  <span class="px-3 py-1 bg-cyan-500/20 text-cyan-300 rounded-full text-sm border border-cyan-500/30">
                    Workflow Automation
                  </span>
                </div>
              </div>
            </div>
          </div>

          <!-- View All Services Button -->
          <div class="pt-6">
            <button
              class="inline-flex items-center px-6 py-3 bg-blue-500 hover:bg-blue-600 text-white rounded-full font-medium transition-colors">
              <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
              </svg>
              View All Services
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const activeAccordion = ref(0) // UI/UX Design expanded by default

const toggleAccordion = (index) => {
  activeAccordion.value = activeAccordion.value === index ? -1 : index
}
</script>

<style scoped>
/* Additional custom styles if needed */
</style>