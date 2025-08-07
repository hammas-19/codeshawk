<template>
  <section class="bg-gray-50 py-12 sm:py-16 lg:py-20 px-4 sm:px-6 lg:px-8">
    <div class="def-container def-padding">
      <!-- Header -->
      <div class="text-center mb-8 sm:mb-12 lg:mb-16">
        <div
          class="inline-flex items-center px-3 sm:px-4 py-2 bg-blue-100 text-blue-600 rounded-full text-xs sm:text-sm font-medium mb-4 sm:mb-6">
          <span class="w-2 h-2 bg-blue-500 rounded-full mr-2" />
          Why choose us
        </div>
        <h2 class="text-2xl sm:text-3xl lg:text-4xl xl:text-5xl font-bold text-gray-900 leading-tight">
          Results that we<br class="hidden sm:block">
          successfully deliver
        </h2>
      </div>

      <!-- Stats Grid -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-4 sm:gap-5">
        <!-- Stats Cards Section -->
        <div class="lg:col-span-2 grid grid-cols-1 sm:grid-cols-2 gap-4 sm:gap-5">
          <!-- Hero Image -->
          <div class="sm:col-span-2 lg:col-span-1 order-1 sm:order-none">
            <img src="/Stats/tileImage.png" class="aspect-square h-full w-full object-cover rounded-xl sm:rounded-2xl"
              alt="">
          </div>

          <!-- Stat Card 1 -->
          <div
            class="bg-white rounded-xl sm:rounded-2xl flex flex-col p-6 sm:p-8 lg:p-12 justify-between h-full min-h-[200px] sm:min-h-[250px] order-2 sm:order-none">
            <div class="flex items-center gap-3">
              <div class="h-2 w-2 rounded-full bg-slateBlue" />
              <p class="text-boss text-sm sm:text-base">projects completed</p>
            </div>
            <div class="flex flex-col gap-2 mt-4 sm:mt-0">
              <p class="text-4xl sm:text-5xl lg:text-6xl text-boss font-normal">
                {{ animatedStats.projects }}+
              </p>
              <p class="text-sm sm:text-base text-gray-600">
                Over 400 successful projects delivered to our
                clients worldwide.
              </p>
            </div>
          </div>

          <!-- Stat Card 2 -->
          <div
            class="bg-white rounded-xl sm:rounded-2xl flex flex-col p-6 sm:p-8 lg:p-12 justify-between h-full min-h-[200px] sm:min-h-[250px] order-3 sm:order-none">
            <div class="flex items-center gap-3">
              <div class="h-2 w-2 rounded-full bg-slateBlue" />
              <p class="text-boss text-sm sm:text-base">client satisfaction</p>
            </div>
            <div class="flex flex-col gap-2 mt-4 sm:mt-0">
              <p class="text-4xl sm:text-5xl lg:text-6xl text-boss font-normal">
                {{ animatedStats.satisfaction }}%
              </p>
              <p class="text-sm sm:text-base text-gray-600">
                Client satisfaction rate based on project
                delivery and quality metrics.
              </p>
            </div>
          </div>

          <!-- Stat Card 3 -->
          <div
            class="bg-white rounded-xl sm:rounded-2xl flex flex-col p-6 sm:p-8 lg:p-12 justify-between h-full min-h-[200px] sm:min-h-[250px] order-4 sm:order-none">
            <div class="flex items-center gap-3">
              <div class="h-2 w-2 rounded-full bg-slateBlue" />
              <p class="text-boss text-sm sm:text-base">hours worked</p>
            </div>
            <div class="flex flex-col gap-2 mt-4 sm:mt-0">
              <p class="text-4xl sm:text-5xl lg:text-6xl text-boss font-normal">
                {{ animatedStats.hours }}K+
              </p>
              <p class="text-sm sm:text-base text-gray-600">
                Total hours invested in delivering
                exceptional results for our clients.
              </p>
            </div>
          </div>
        </div>

        <!-- Group Image -->
        <div class="order-5 sm:order-none">
          <img src="/Stats/groupImage.png" class="h-64 sm:h-80 lg:h-full w-full rounded-2xl sm:rounded-3xl object-cover"
            alt="">
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const animatedStats = ref({
  projects: 0,
  satisfaction: 0,
  hours: 0
})

const targetStats = {
  projects: 475,
  satisfaction: 98,
  hours: 843
}

const animateNumber = (target, current, key, duration = 2000) => {
  const increment = target / (duration / 16) // 60fps
  const timer = setInterval(() => {
    current += increment
    if (current >= target) {
      animatedStats.value[key] = target
      clearInterval(timer)
    } else {
      animatedStats.value[key] = Math.floor(current)
    }
  }, 16)
}

onMounted(() => {
  // Animate numbers on mount
  setTimeout(() => {
    animateNumber(targetStats.projects, 0, 'projects')
    animateNumber(targetStats.satisfaction, 0, 'satisfaction')
    animateNumber(targetStats.hours, 0, 'hours')
  }, 500)
})
</script>

<style scoped>
/* Custom animations can be added here if needed */
</style>