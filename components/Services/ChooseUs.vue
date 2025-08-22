<template>
  <div class="def-container def-margin-full bg-white rounded-3xl def-padding-full relative">
    <h2
      class="text-center xl:text-[145px] lg:text-[110px] md:text-[87px] sm:text-[50px] text-[35px] uppercase leading-0 absolute inset-0 w-full sm:font-medium font-black text-white xl:-top-[4.8%] lg:-top-[3.7%] md:-top-[2%] sm:-top-[1.4%] -top-2">
      why choose us
    </h2>
    <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 mb-10">
      <div class="flex sm:flex-row flex-col justify-between gap-12 lg:gap-16">
        <!-- Left Side - Small Indicator -->
        <div class="flex-shrink-0 pt-2 sticky top-0 h-fit">
          <div class="flex items-center space-x-2 bg-white px-4 py-2 rounded-full shadow-sm border w-fit">
            <div class="w-2 h-2 bg-slateBlue rounded-full" />
            <span class="text-boss font-medium text-sm tracking-wide">Why choose us</span>
          </div>
        </div>

        <!-- Right Side - Content with Max Width -->
        <div class="flex-1 max-w-3xl">
          <!-- Main Heading -->
          <h2 class="text-4xl md:text-5xl lg:text-6xl font-medium text-gray-900 mb-8 md:text-right">
            Reimagined user
            experiences
          </h2>
        </div>
      </div>
    </div>
    <div class="max-w-5xl mx-auto w-full flex lg:flex-row flex-col gap-10 justify-between items-center">
      <img
        src="https://images.unsplash.com/photo-1525015582196-5316b8a0afc9?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
        class="rounded-3xl md:max-h-[600px] max-h-[200px] h-full md:w-2/5 w-full object-cover" alt="">

      <!-- POINTS -->
      <div class="w-full max-w-[500px] flex flex-col gap-10">
        <template v-for="(point, index) in points" :key="index">
          <div class="space-y-4 transition-opacity duration-700 ease-in-out cursor-pointer"
            :class="getOpacityClass(index)" @mouseenter="handleMouseEnter(index)" @mouseleave="handleMouseLeave">
            <h3 class="text-2xl text-black font-semibold">{{ point.title }}</h3>
            <p class="text-darkLiver md:text-xl text-base">
              {{ point.description }}
            </p>
          </div>
          <div v-if="index < points.length - 1" class="w-full border-t border-[#DFDEE5]" />
        </template>
      </div>
    </div>
  </div>
</template>

<script setup>
const activeIndex = ref(0)
const hoveredIndex = ref(null)
const isHovered = ref(false)
let autoplayInterval = null

const points = [
  {
    title: "Customized Solutions",
    description: "Building strong media connections to elevate your brand's visibility and credibility."
  },
  {
    title: "Expert Teams",
    description: "We're a team of strategic working globally with largest brands, We believe that progress only happens."
  },
  {
    title: "Improved Performance",
    description: "Crafting brand strategies to establish a strong and lasting market presence."
  }
]

const getOpacityClass = (index) => {
  if (isHovered.value) {
    return hoveredIndex.value === index ? 'opacity-100' : 'opacity-40'
  }
  return activeIndex.value === index ? 'opacity-100' : 'opacity-40'
}

const handleMouseEnter = (index) => {
  isHovered.value = true
  hoveredIndex.value = index
  if (autoplayInterval) {
    clearInterval(autoplayInterval)
    autoplayInterval = null
  }
}

const handleMouseLeave = () => {
  isHovered.value = false
  hoveredIndex.value = null
  startAutoplay()
}

const startAutoplay = () => {
  if (autoplayInterval) {
    clearInterval(autoplayInterval)
  }
  autoplayInterval = setInterval(() => {
    if (!isHovered.value) {
      activeIndex.value = (activeIndex.value + 1) % points.length
    }
  }, 4000)
}

onMounted(() => {
  startAutoplay()
})

onUnmounted(() => {
  if (autoplayInterval) {
    clearInterval(autoplayInterval)
  }
})
</script>