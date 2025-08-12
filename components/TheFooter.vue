<template>
  <div class="m-2">
    <footer class="bg-cobalt text-white md:rounded-4xl rounded-2xl ">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16 relative z-50">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 mb-16">
          <!-- Left Section -->
          <div class="space-y-8">
            <div>
              <h3 class="text-lg font-medium text-blue-200 mb-4">Tell us about your project</h3>
              <h2 class="text-5xl md:text-6xl lg:text-7xl font-bold leading-tight">
                Let's talk
              </h2>
            </div>
          </div>

          <!-- Right Section -->
          <div class="space-y-8">
            <!-- Newsletter Signup -->
            <div>
              <h3 class="text-lg font-medium text-blue-200 mb-6">Get the latest inspiration & insights</h3>
              <form @submit.prevent="handleNewsletterSubmit" class="flex gap-2">
                <div class="flex-1 relative">
                  <input v-model="email" type="email" placeholder="Your Email..." required
                    class="w-full px-6 py-4 rounded-full bg-white text-gray-900 placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-blue-400 transition-all duration-200" />
                </div>
                <button type="submit"
                  class="px-6 py-4 bg-blue-600 hover:bg-blue-700 rounded-full transition-all duration-200 hover:scale-105 flex items-center justify-center min-w-[60px]">
                  <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                      d="M17 8l4 4m0 0l-4 4m4-4H3" />
                  </svg>
                </button>
              </form>
            </div>

            <!-- Navigation Links -->
            <div class="grid grid-cols-2 gap-8 pt-8">
              <!-- First Column -->
              <div class="space-y-4">
                <NuxtLink to="/"
                  class="block text-gray-300 hover:text-white transition-colors duration-200 hover:translate-x-1 transform">
                  Home
                </NuxtLink>
                <NuxtLink to="/about"
                  class="block text-gray-300 hover:text-white transition-colors duration-200 hover:translate-x-1 transform">
                  About Us
                </NuxtLink>
                <NuxtLink to="/portfolio"
                  class="block text-gray-300 hover:text-white transition-colors duration-200 hover:translate-x-1 transform">
                  Portfolio
                </NuxtLink>
              </div>

              <!-- Second Column -->
              <div class="space-y-4">
                <NuxtLink to="/services"
                  class="block text-gray-300 hover:text-white transition-colors duration-200 hover:translate-x-1 transform">
                  Services
                </NuxtLink>
                <NuxtLink to="/blog"
                  class="block text-gray-300 hover:text-white transition-colors duration-200 hover:translate-x-1 transform">
                  Blog
                </NuxtLink>
                <NuxtLink to="/contact"
                  class="block text-gray-300 hover:text-white transition-colors duration-200 hover:translate-x-1 transform">
                  Contact
                </NuxtLink>
              </div>
            </div>

            <!-- Contact Info -->
            <div class="pt-8">
              <h4 class="text-lg font-medium text-blue-200 mb-4">Head office</h4>
              <div class="space-y-2 text-gray-300">
                <p>2972 Westheimer Rd. Santa Ana,</p>
                <p>Illinois 85486</p>
                <p class="pt-2">
                  <a href="mailto:support@example.com" class="hover:text-white transition-colors duration-200">
                    support@example.com
                  </a>
                </p>
                <p>
                  <a href="tel:+14065550120" class="hover:text-white transition-colors duration-200">
                    + (406) 555-0120
                  </a>
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- Bottom Section -->
        <div class="border-t border-blue-800 pt-8">
          <div class="flex flex-col md:flex-row justify-between items-center gap-6">
            <!-- Copyright -->
            <div class="flex items-center space-x-2 text-gray-400">
              <span>© 2025</span>
              <NuxtLink to="/" class="text-blue-400 hover:text-blue-300 transition-colors duration-200 font-medium">
                Codes Hawk
              </NuxtLink>
              <span>. All Rights Reserved.</span>
            </div>

            <!-- Social Links -->
            <div class="flex items-center md:space-x-6 space-x-2 ">
              <span class="text-gray-400">Follow Us</span>
              <div class="flex items-center md:space-x-4 space-x-2 flex-wrap">
                <a href="https://facebook.com" target="_blank" rel="noopener noreferrer"
                  class="text-gray-400 hover:text-white transition-all duration-200 hover:scale-110">
                  Facebook
                </a>
                <span class="text-gray-600">•</span>
                <a href="https://instagram.com" target="_blank" rel="noopener noreferrer"
                  class="text-gray-400 hover:text-white transition-all duration-200 hover:scale-110">
                  Instagram
                </a>
                <span class="text-gray-600">•</span>
                <a href="https://youtube.com" target="_blank" rel="noopener noreferrer"
                  class="text-gray-400 hover:text-white transition-all duration-200 hover:scale-110">
                  Youtube
                </a>
                <span class="text-gray-600">•</span>
                <a href="https://tiktok.com" target="_blank" rel="noopener noreferrer"
                  class="text-gray-400 hover:text-white transition-all duration-200 hover:scale-110">
                  Tiktok
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
// Reactive state
const email = ref('')

// Methods
const handleNewsletterSubmit = () => {
  if (!email.value) return

  // Handle newsletter signup logic here
  console.log('Newsletter signup:', email.value)

  // Show success message or handle API call
  // For now, just clear the email
  email.value = ''

  // You can add a toast notification here
  // toast.success('Successfully subscribed to newsletter!')
}
</script>

<style scoped>
/* Custom gradient animation for the background */
.bg-gradient-to-br {
  background-size: 200% 200%;
  animation: gradientShift 8s ease infinite;
}

@keyframes gradientShift {
  0% {
    background-position: 0% 50%;
  }

  50% {
    background-position: 100% 50%;
  }

  100% {
    background-position: 0% 50%;
  }
}

/* Smooth hover effects */
a,
button {
  transition: all 0.2s ease-in-out;
}
</style>