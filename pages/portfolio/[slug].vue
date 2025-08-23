<template>
  <div class="min-h-screen bg-antiFlash">
    <!-- Header Section -->
    <section class="py-8 px-4 sm:px-6 lg:px-8">
      <div>
        <!-- Category Badge -->
        <div class="flex justify-center mb-6">
          <div class="inline-flex items-center px-3 py-1 bg-[#636ddf1f] rounded-full">
            <div class="w-2 h-2 bg-slateBlue rounded-full mr-2"></div>
            <span class="text-sm font-medium text-slateBlue">{{ project.category }}</span>
          </div>
        </div>

        <!-- Project Title -->
        <div class="text-center mb-8">
          <h1 class="text-5xl md:text-7xl lg:text-8xl font-normal text-black mb-12 leading-tight">
            {{ project.title }}
          </h1>
        </div>

        <!-- Project Meta Info -->
        <div class="grid grid-cols-4 gap-8 mb-12 text-center def-container">
          <div>
            <h3 class="text-sm font-medium text-gray-500 mb-2">{{ project.meta.dateLabel }}</h3>
            <p class="text-base font-medium text-black">{{ project.meta.date }}</p>
          </div>
          <div>
            <h3 class="text-sm font-medium text-gray-500 mb-2">{{ project.meta.clientLabel }}</h3>
            <p class="text-base font-medium text-black">{{ project.meta.client }}</p>
          </div>
          <div>
            <h3 class="text-sm font-medium text-gray-500 mb-2">{{ project.meta.categoryLabel }}</h3>
            <p class="text-base font-medium text-black">{{ project.meta.categoryValue }}</p>
          </div>
          <div>
            <h3 class="text-sm font-medium text-gray-500 mb-2">{{ project.meta.locationLabel }}</h3>
            <p class="text-base font-medium text-black">{{ project.meta.location }}</p>
          </div>
        </div>

        <!-- Hero Image -->
        <div class="w-full md:rounded-[40px] rounded-3xl overflow-hidden">
          <img :src="project.heroImage" :alt="project.title" class="w-full h-[500px] md:h-[600px] object-cover">
        </div>
      </div>
    </section>

    <div class="def-container">

      <!-- Project Description -->
      <section class="py-16 ">
        <div class=" mx-auto">
          <p class="text-lg md:text-2xl leading-relaxed text-black">
            {{ project.description }}
          </p>
        </div>
      </section>

      <!-- Challenge & Solution and Our Process -->
      <section class="py-16">
        <div class="max-w-6xl mx-auto">
          <div class="grid md:grid-cols-2 gap-16 mb-10">
            <!-- Challenge & Solution -->
            <div>
              <h2 class="text-3xl md:text-4xl font-medium text-black mb-8">Challenge &<br>Solution</h2>
            </div>
            <div>
              <p class="text-gray-600 mb-8 leading-relaxed">
                {{ project.challenge.description }}
              </p>
              <div class="divide-y divide-[#DDDDDD]">
                <div v-for="step in project.challenge.steps" :key="step" class="text-black text-xl py-4">
                  {{ step }}
                </div>
              </div>
            </div>
          </div>

          <!-- Our Process -->
          <hr class="mb-10 text-[#DDDDDD]">
          <div class="grid md:grid-cols-2 gap-16">
            <div>
              <h2 class="text-3xl md:text-4xl font-medium text-black mb-8">Our Process</h2>
            </div>
            <div>
              <p class="text-gray-600 leading-relaxed">
                {{ project.process.description }}
              </p>
            </div>
          </div>
        </div>
      </section>

      <!-- Process Images -->
      <section class="py-16">
        <div class="max-w-6xl mx-auto">
          <div class="grid md:grid-cols-2 gap-8">
            <div class="rounded-2xl overflow-hidden bg-gray-800">
              <img :src="project.process.images[0]" alt="Process Image 1" class="w-full h-96 object-cover">
            </div>
            <div class="rounded-2xl overflow-hidden bg-gray-600">
              <img :src="project.process.images[1]" alt="Process Image 2" class="w-full h-96 object-cover">
            </div>
          </div>
        </div>
      </section>

      <!-- Result Driven -->
      <hr class="text-[#DDDDDD]">
      <section class="py-16">
        <div class="max-w-6xl mx-auto">
          <div class="grid md:grid-cols-2 gap-16">
            <div>
              <h2 class="text-3xl md:text-4xl font-medium text-black mb-8">Result Driven</h2>
            </div>
            <div>
              <p class="text-gray-600 mb-8 leading-relaxed">
                {{ project.results.description }}
              </p>
              <div class="space-y-6 divide-y divide-[#DDDDDD]">
                <div v-for="result in project.results.achievements" :key="result" class="text-black text-xl py-4">
                  {{ result }}
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>

    <!-- Navigation -->
    <section class="py-12">
      <div class="max-w-6xl mx-auto">
        <div class="flex justify-between items-center">
          <button class="flex items-center text-black font-medium hover:opacity-70 transition-opacity text-lg">
            <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
            </svg>
            previous project
          </button>
          <button class="flex items-center text-black font-medium hover:opacity-70 transition-opacity text-lg">
            next project
            <svg class="w-5 h-5 ml-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
            </svg>
          </button>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
// Sample project data
const project = {
  title: "Social Media Campaigns",
  category: "Development",
  heroImage: "https://plus.unsplash.com/premium_photo-1729036163578-f80877183448?q=80&w=1074&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate.",
  meta: {
    dateLabel: "Date",
    date: "27 August, 2024",
    clientLabel: "Client",
    client: "Logistic Company",
    categoryLabel: "Category",
    categoryValue: "Development",
    locationLabel: "Location",
    location: "New York, USA"
  },
  challenge: {
    description: "Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt.",
    steps: [
      "Research",
      "Concept Design",
      "Implementation"
    ]
  },
  process: {
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
    images: [
      "https://images.unsplash.com/photo-1460925895917-afdab827c52f?q=80&w=800&auto=format&fit=crop",
      "https://images.unsplash.com/photo-1542744173-8e7e53415bb0?q=80&w=800&auto=format&fit=crop"
    ]
  },
  results: {
    description: "Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt.",
    achievements: [
      "Branding and identity",
      "Websites and digital platforms",
      "Content strategy for social media"
    ]
  }
}
</script>