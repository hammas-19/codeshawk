<template>
  <section class="bg-gray-50 py-20 px-4 sm:px-6 lg:px-8">
    <div class="def-container def-padding ">
      <!-- Header -->
      <div class="text-center mb-16">
        <div class="inline-flex items-center px-4 py-2 bg-blue-100 text-blue-600 rounded-full text-sm font-medium mb-6">
          <span class="w-2 h-2 bg-blue-500 rounded-full mr-2"/>
          Why choose us
        </div>
        <h2 class="text-4xl lg:text-5xl font-bold text-gray-900 leading-tight">
          Results that we<br>
          successfully deliver
        </h2>
      </div>
      <div class=" grid grid-cols-3 gap-5">
        <div class="col-span-2 grid grid-cols-2 gap-5">
          <img src="/Stats/tileImage.png" class="aspect-square h-full w-full object-cover rounded-2xl" alt="">
          <div class="bg-white rounded-2xl flex flex-col p-12 justify-between h-full">
            <div class="flex items-baseline-last gap-3">
              <div class="h-2 w-2 rounded-full bg-slateBlue"/>
              <p class="text-boss">projects completed</p>
            </div>
            <div class="flex flex-col gap-2">
              <p class="text-6xl text-boss font-normal">
                475 +
              </p>
              <p>
                Over 400 successful projects delivered to our
                clients worldwide.
              </p>
            </div>
          </div>
          <div class="bg-white rounded-2xl flex flex-col p-12 justify-between h-full">
            <div class="flex items-baseline-last gap-3">
              <div class="h-2 w-2 rounded-full bg-slateBlue"/>
              <p class="text-boss">projects completed</p>
            </div>
            <div class="flex flex-col gap-2">
              <p class="text-6xl text-boss font-normal">
                475 +
              </p>
              <p>
                Over 400 successful projects delivered to our
                clients worldwide.
              </p>
            </div>
          </div>
          <div class="bg-white rounded-2xl flex flex-col p-12 justify-between h-full">
            <div class="flex items-baseline-last gap-3">
              <div class="h-2 w-2 rounded-full bg-slateBlue"/>
              <p class="text-boss">projects completed</p>
            </div>
            <div class="flex flex-col gap-2">
              <p class="text-6xl text-boss font-normal">
                475 +
              </p>
              <p>
                Over 400 successful projects delivered to our
                clients worldwide.
              </p>
            </div>
          </div>
        </div>
        <img src="/Stats/groupImage.png" class="h-full w-full rounded-3xl object-cover" alt="">
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