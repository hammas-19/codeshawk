<template>
  <!-- Top navbar with logo and CTA (scrolls away) -->
  <nav class="relative z-40 transition-all duration-300"
    :class="scrolled ? 'bg-white/90 backdrop-blur-lg shadow-lg' : 'bg-transparent'">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-14 sm:h-16">
        <!-- Logo -->
        <div class="flex items-center">
          <NuxtLink to="/" class="flex items-center space-x-2 group">
            <span class="text-lg sm:text-xl font-bold transition-colors duration-200"
              :class="scrolled ? 'text-gray-800 group-hover:text-blue-600' : 'text-white group-hover:text-blue-200'">
              <svg width="140" height="22" sm:width="198" sm:height="31" viewBox="0 0 198 31" fill="none"
                xmlns="http://www.w3.org/2000/svg" class="h-6 sm:h-8 w-auto">
                <g clip-path="url(#clip0_5_1933)">
                  <g clip-path="url(#clip1_5_1933)">
                    <g clip-path="url(#clip2_5_1933)">
                      <path
                        d="M44.968 18.0145V23.2845C44.968 25.0072 44.5827 26.2538 43.812 27.0245C43.064 27.7725 41.8173 28.1465 40.072 28.1465H38.576C36.8307 28.1465 35.5727 27.7725 34.802 27.0245C34.054 26.2538 33.68 25.0072 33.68 23.2845V8.66451C33.68 6.91918 34.054 5.67251 34.802 4.92451C35.5727 4.17651 36.8307 3.80251 38.576 3.80251H40.072C41.8173 3.80251 43.064 4.17651 43.812 4.92451C44.5827 5.67251 44.968 6.91918 44.968 8.66451V14.2745L40.344 13.7645V8.49451C40.344 8.38118 40.2873 8.32451 40.174 8.32451H38.474C38.3607 8.32451 38.304 8.38118 38.304 8.49451V23.4545C38.304 23.5678 38.3607 23.6245 38.474 23.6245H40.174C40.2873 23.6245 40.344 23.5678 40.344 23.4545V18.0145H44.968ZM57.6184 23.1485C57.6184 24.8712 57.2331 26.1178 56.4624 26.8885C55.7144 27.6365 54.4677 28.0105 52.7224 28.0105H51.2264C49.4811 28.0105 48.2231 27.6365 47.4524 26.8885C46.7044 26.1178 46.3304 24.8712 46.3304 23.1485V8.80051C46.3304 7.05518 46.7044 5.80851 47.4524 5.06051C48.2231 4.31251 49.4811 3.93851 51.2264 3.93851H52.7224C54.4677 3.93851 55.7144 4.31251 56.4624 5.06051C57.2331 5.80851 57.6184 7.05518 57.6184 8.80051V23.1485ZM51.1244 8.46051C51.0111 8.46051 50.9544 8.51718 50.9544 8.63051V23.3185C50.9544 23.4318 51.0111 23.4885 51.1244 23.4885H52.8244C52.9377 23.4885 52.9944 23.4318 52.9944 23.3185V8.63051C52.9944 8.51718 52.9377 8.46051 52.8244 8.46051H51.1244ZM70.7488 23.0125C70.7488 24.7352 70.3634 25.9818 69.5928 26.7525C68.8448 27.5005 67.5981 27.8745 65.8528 27.8745H59.4608V8.59651H58.8148L59.2908 4.07451H65.8528C67.5981 4.07451 68.8448 4.44851 69.5928 5.19651C70.3634 5.94451 70.7488 7.19118 70.7488 8.93651V23.0125ZM65.9548 23.3525C66.0681 23.3525 66.1248 23.2958 66.1248 23.1825V8.76651C66.1248 8.65318 66.0681 8.59651 65.9548 8.59651H64.0848V23.3525H65.9548ZM72.41 27.8745V8.59651H71.764L72.24 4.07451H81.964L81.692 8.59651H77.034V13.6965H81.216L80.944 18.2185H77.034V23.3525H81.964L81.692 27.8745H72.41ZM87.7727 20.3945V23.4545C87.7727 23.5678 87.8293 23.6245 87.9427 23.6245H88.9287C89.042 23.6245 89.0987 23.5678 89.0987 23.4545L89.1327 18.9325L85.2907 17.2665C84.4293 16.8812 83.8513 16.4845 83.5567 16.0765C83.2847 15.6685 83.1487 15.0452 83.1487 14.2065V8.66451C83.1487 6.91918 83.5227 5.67251 84.2707 4.92451C85.0187 4.17651 86.2313 3.80251 87.9087 3.80251H89.3367C90.9233 3.87051 92.0567 4.28984 92.7367 5.06051C93.4167 5.80851 93.7567 7.00984 93.7567 8.66451V12.9145L89.1327 12.4045V8.49451C89.1327 8.38118 89.076 8.32451 88.9627 8.32451H87.9427C87.8293 8.32451 87.7727 8.38118 87.7727 8.49451V13.4925L91.6147 15.1585C92.476 15.5212 93.0427 15.9178 93.3147 16.3485C93.6093 16.7565 93.7567 17.3798 93.7567 18.2185V23.2845C93.7567 24.9392 93.4167 26.1518 92.7367 26.9225C92.0567 27.6705 90.9233 28.0785 89.3367 28.1465H87.9767C86.254 28.1465 85.0187 27.7725 84.2707 27.0245C83.5227 26.2538 83.1487 25.0072 83.1487 23.2845V20.3945H87.7727ZM95.5858 27.8745V8.59651H94.9398L95.4158 4.07451H100.21V14.4105H102.08V4.07451H106.704V27.8745H102.08V18.9325H100.21V27.8745H95.5858ZM108.055 27.8745L110.877 8.59651H110.163L110.639 4.07451H118.561L122.063 27.8745H117.473L116.963 24.4745H113.155L112.645 27.8745H108.055ZM113.801 19.9525H116.317L115.059 11.4525L113.801 19.9525ZM123.598 27.8745V4.07451H128.222V18.8985L130.126 7.47451H133.356L135.158 18.2865V4.07451H139.782V27.8745H133.39L131.724 15.0565L130.092 27.8745H123.598ZM141.805 27.8745V8.59651H141.159L141.635 4.07451H146.429V10.2965L149.353 4.07451H153.773L149.115 14.0025L154.385 27.8745H149.965L146.429 18.5585V27.8745H141.805Z"
                        fill="black" />
                      <path
                        d="M29.9267 1.91722C29.8407 1.5903 29.679 1.29539 29.4633 1.05105L29.4557 1.04346C29.2096 0.824393 28.9114 0.660932 28.5827 0.572462C28.405 0.525277 28.2187 0.5 28.0241 0.5H17.2464C16.0558 0.5 15.091 1.46475 15.091 2.65532V13.4386C15.0927 13.8262 14.9562 14.2003 14.6815 14.475L13.9771 15.1794C13.7024 15.4541 13.3283 15.5906 12.9407 15.5889H2.15622C2.01803 15.5889 1.88322 15.6015 1.75177 15.6268C0.986687 15.7726 0.364847 16.3203 0.118807 17.0423C0.0412875 17.2614 0 17.4982 0 17.7451V28.5233C0 28.7171 0.0252781 28.9042 0.0733064 29.0819C0.159252 29.4089 0.321031 29.7038 0.536738 29.9481L0.544321 29.9557C0.790361 30.1748 1.08864 30.3382 1.41726 30.4267C1.59505 30.4756 1.7821 30.5 1.9759 30.5H12.7545C13.9451 30.5 14.9098 29.5352 14.9098 28.3447V17.5597C14.9082 17.1721 15.0447 16.798 15.3193 16.5233L16.0238 15.8189C16.2984 15.5442 16.6726 15.4077 17.0602 15.4094H27.8438C27.982 15.4094 28.1168 15.3968 28.2482 15.3715C29.0133 15.2257 29.6352 14.6781 29.8812 13.956C29.9587 13.7369 30 13.5001 30 13.2533V2.47585C30 2.28205 29.9756 2.095 29.9267 1.91722Z"
                        fill="#636EDF" />
                    </g>
                  </g>
                </g>
                <defs>
                  <clipPath id="clip0_5_1933">
                    <rect width="155" height="30" fill="white" transform="translate(0 0.5)" />
                  </clipPath>
                  <clipPath id="clip1_5_1933">
                    <rect width="155" height="30" fill="white" transform="translate(0 0.5)" />
                  </clipPath>
                  <clipPath id="clip2_5_1933">
                    <rect width="155" height="30" fill="white" transform="translate(0 0.5)" />
                  </clipPath>
                </defs>
              </svg>
            </span>
          </NuxtLink>
        </div>

        <!-- Desktop CTA & Mobile Menu Toggle -->
        <div class="flex items-center space-x-2 sm:space-x-4">
          <!-- Theme Button - Hidden on mobile -->
          <div class="hidden sm:block">
            <ThemeBtn class="border border-[#DFDEE5]" />
          </div>

          <!-- Mobile menu button -->
          <button @click="toggleMobileMenu"
            class="md:hidden p-2 rounded-lg transition-all duration-200 hover:scale-110 touch-manipulation"
            :class="scrolled ? 'hover:bg-gray-100 text-gray-600' : 'hover:bg-white/10 text-white'">
            <svg v-if="!showMobileMenu" class="w-5 h-5 sm:w-6 sm:h-6" fill="none" stroke="currentColor"
              viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
            <svg v-else class="w-5 h-5 sm:w-6 sm:h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Navigation -->
    <div v-show="showMobileMenu"
      class="md:hidden bg-white border-t border-gray-100 shadow-lg transition-all duration-300 max-h-screen overflow-y-auto"
      :class="showMobileMenu ? 'opacity-100 translate-y-0' : 'opacity-0 -translate-y-4'">
      <div class="px-4 py-4 space-y-1">
        <!-- Main Navigation Links -->
        <NuxtLink v-for="item in navigationItems" :key="item.name" :to="item.href"
          class="block px-4 py-3 text-base font-medium text-gray-700 hover:text-blue-600 hover:bg-gray-50 rounded-lg transition-all duration-200 touch-manipulation"
          :class="{ 'text-blue-600 bg-blue-50': $route.path === item.href }" @click="showMobileMenu = false">
          {{ item.name }}
        </NuxtLink>

        <!-- Mobile Theme Button -->
        <div class="px-4 py-2 sm:hidden">
          <div class="flex items-center justify-between">
            <span class="text-base font-medium text-gray-700">Theme</span>
            <ThemeBtn />
          </div>
        </div>

        <!-- Mobile CTA -->
        <div class="px-4 pt-4 border-t border-gray-100">
          <NuxtLink to="/contact"
            class="flex items-center justify-center w-full px-6 py-3 bg-gradient-to-r from-blue-500 to-purple-600 text-white rounded-lg hover:from-blue-600 hover:to-purple-700 transition-all duration-200 text-base font-medium touch-manipulation"
            @click="showMobileMenu = false">
            <span>Get Started</span>
            <svg class="w-4 h-4 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
            </svg>
          </NuxtLink>
        </div>
      </div>
    </div>
  </nav>

  <!-- Fixed Center Navigation (Desktop and Tablet only) -->
  <div class="hidden lg:block fixed top-2 left-1/2 transform -translate-x-1/2 z-50 transition-all duration-300">
    <div class="flex items-center space-x-1 px-4 py-2 rounded-full transition-all duration-300"
      :class="scrolled ? 'bg-white shadow-lg' : 'bg-white/0 backdrop-blur-lg'">
      <NuxtLink v-for="item in navigationItems" :key="item.name" :to="item.href"
        class="relative px-4 py-2 transition-all duration-200 group rounded-lg hover:-translate-y-0.5" :class="[
          $route.path === item.href
            ? (scrolled ? 'text-blue-600' : 'text-black bg-white/30 backdrop-blur-2xl')
            : (scrolled ? 'text-gray-700 hover:text-blue-600' : 'text-black/80 hover:text-clearBlue')
        ]">
        <span class="relative z-10 text-sm lg:text-base">{{ item.name }}</span>
        <div class="absolute inset-0 rounded-lg opacity-0 group-hover:opacity-100 transition-opacity duration-200"
          :class="scrolled ? 'bg-blue-50' : 'bg-white/10'"></div>
        <div v-if="$route.path === item.href"
          class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-6 h-0.5 rounded-full transition-colors duration-200"
          :class="scrolled ? 'bg-blue-600' : 'bg-slateBlue'"></div>
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
const route = useRoute()

// Reactive state
const showMobileMenu = ref(false)
const scrolled = ref(false)

// Navigation items - Services added as normal link
const navigationItems = [
  { name: 'Home', href: '/' },
  { name: 'About Us', href: '/about' },
  { name: 'Services', href: '/services' },
  { name: 'Case Studies', href: '/case-studies' },
  { name: 'Contact Us', href: '/contact' }
]

// Methods
const toggleMobileMenu = () => {
  showMobileMenu.value = !showMobileMenu.value
  if (showMobileMenu.value) {
    // Prevent body scroll when menu is open
    document.body.style.overflow = 'hidden'
  } else {
    // Restore body scroll
    document.body.style.overflow = ''
  }
}

// Handle scroll effect
const handleScroll = () => {
  scrolled.value = window.scrollY > 10
}

// Handle click outside to close dropdowns
const handleClickOutside = (event) => {
  // No dropdowns to close anymore
}

// Lifecycle hooks
onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  document.addEventListener('click', handleClickOutside)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  document.removeEventListener('click', handleClickOutside)
  // Ensure body scroll is restored
  document.body.style.overflow = ''
})

// Watch for route changes to close mobile menu
watch(() => route.path, () => {
  showMobileMenu.value = false
  document.body.style.overflow = ''
})
</script>