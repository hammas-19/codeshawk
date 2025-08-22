<template>
  <section class="bg-antiFlash px-5 def-padding-full">
    <div class="def-container">
      <section class="mb-10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="flex sm:flex-row flex-col justify-between gap-12 lg:gap-16">
            <!-- Left Side - Small Indicator -->
            <div class="flex-shrink-0 pt-2 sticky top-0 h-fit">
              <div class="flex items-center space-x-2 bg-white px-4 py-2 rounded-full shadow-sm border w-fit">
                <div class="w-2 h-2 bg-slateBlue rounded-full"></div>
                <span class="text-boss font-medium text-sm tracking-wide">What we do</span>
              </div>
            </div>

            <!-- Right Side - Content with Max Width -->
            <div class="flex-1 max-w-3xl">
              <!-- Main Heading -->
              <h2 class="text-4xl md:text-5xl lg:text-6xl font-medium text-gray-900 mb-8">
                Innovative digital
                solution services
              </h2>
            </div>
          </div>
        </div>
      </section>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="service in services" :key="service.id" class=" p-8 rounded-xl border border-[#DFDEE5]">
          <img :src="service.icon" class="mb-5" :alt="service.title">
          <h3 class="md:text-[32px] text-2xl  mb-4 text-black">{{ service.title }}</h3>
          <p class="text-darkLiver text-sm">{{ service.description }}</p>
          <hr class="my-10 text-[#DFDEE5]">
          <ThemeBtn :text="'Learn More'" :small="true" :white-bg="false" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const services = [
  {
    id: 1,
    icon: '/Serices/icon1.svg',
    title: 'Advanced Analytics',
    description: 'Our strategic solutions unlock opportunities and solve business problems.'
  },
  {
    id: 2,
    icon: '/Serices/icon2.svg',
    title: 'Marketing Strategy',
    description: 'We combine audience insights with our strategic expertise.'
  },
  {
    id: 3,
    icon: '/Serices/icon3.svg',
    title: 'System and Software',
    description: 'We prototype interaction, animation and experiences to bring UI to life.'
  },
  {
    id: 4,
    icon: '/Serices/icon4.svg',
    title: 'Digital Strategy',
    description: 'Design is at the heart of everything we do, with every solution tailored to the needs of each client.'
  },
  {
    id: 5,
    icon: '/Serices/icon5.svg',
    title: 'Web Development',
    description: 'Creative yet functional, we develop comprehensive Design Systems.'
  },
  {
    id: 6,
    icon: '/Serices/icon6.svg',
    title: 'Brand Identity',
    description: 'Visuals and aesthetics are the best tools to communicate effectively.'
  },
  {
    id: 7,
    icon: '/Serices/icon7.svg',
    title: 'UX/UI Design',
    description: 'We elevate user experiences through meticulous research and creative design.'
  }
]
</script>