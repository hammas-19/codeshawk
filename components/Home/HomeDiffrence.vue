<template>
  <section class="py-16 md:py-24">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="flex justify-between md:items-center mb-12 md:flex-row flex-col-reverse gap-2">
        <h2 class="text-4xl md:text-5xl text-gray-900">
          Key Differentiators
        </h2>
        <div>
          <ThemeBtn class="md:block hidden" :to="'/contact'" :text="'Learn More'" />
          <ThemeBtn class="md:hidden block self-end place-self-end" :small="true" :to="'/contact'" :text="'Learn More'" />
        </div>
      </div>

      <!-- Cards Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        <!-- Card 1: Tailored Solutions -->
        <div v-for="(items, index) in data" :key="index"
          class="bg-white rounded-2xl p-8 hover:shadow-lg transition-all duration-300 hover:-translate-y-1 flex flex-col justify-between gap-3">
          <img :src="items.icon" class="md:h-22 h-16 w-fit" alt="Tailored Solutions">
          <div class="">
            <h3 class="text-2xl text-black my-4">
              {{ items.title }}
            </h3>
            <p class="text-gray-600 text-sm md:text-base leading-relaxed">
              {{ items.desc }}
            </p>
          </div>
        </div>
        <!-- Card 4: Free Advice -->
         <div class="h-full relative">
          <ThemeBtn :small="true" :to="'/contact'" class="absolute bottom-0 right-0" />
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
             <img src="/CTA/CTA1.png" class="max-w-[320px] h-fit px-8 mt-10 relative z-0" alt="">
            </div>
          </div>
      </div>

      <!-- Mobile CTA -->
      <!-- <div class="md:hidden mt-8 text-center">
        <button
          class="flex items-center space-x-2 px-6 py-3 bg-blue-600 text-white rounded-full hover:bg-blue-700 transition-all duration-200 hover:scale-105 mx-auto">
          <span class="font-medium">Learn More About Our Story</span>
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
          </svg>
        </button>
      </div> -->
    </div>
  </section>
</template>

<script setup>
const data = [
  {
    icon: '/keyDiff/tailored.svg',
    title: 'Tailored Solutions',
    desc: 'Every business is unique. We listen intently to your challenges and craft custom strategies, ensuring our solutions perfectly fit your specific needs and drive tangible results.'
  },
  {
    icon: '/keyDiff/expertTeam.svg',
    title: 'Expert Team',
    desc: 'Our diverse team comprises seasoned web developers, UI/UX designers, AI specialists, digital marketers, and content strategists, all united by a passion for technology and a commitment to excellence.'
  },
  {
    icon: '/keyDiff/resultDriven.svg',
    title: 'Results-Driven Approach',
    desc: 'Your success is our ultimate measure. We focus on delivering solutions that not only look great but also perform exceptionally, contributing directly to your growth and ROI.'
  }
]
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
.inverted-radius {
  --r: 15px;
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