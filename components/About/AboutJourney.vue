<template>
  <section class="relative min-h-screen bg-cobalt overflow-hidden m-2 md:rounded-4xl rounded-2xl">
    <!-- Background overlay for depth -->
    <div class="absolute inset-0 bg-black/20" />

    <!-- Decorative background elements -->
    <div class="absolute top-20 left-10 w-32 h-32 bg-blue-400/10 rounded-full blur-xl" />
    <div class="absolute bottom-40 right-20 w-48 h-48 bg-purple-400/10 rounded-full blur-2xl" />

    <div class="relative z-10 container mx-auto px-6 py-16">
      <!-- Top navigation button -->
      <div class="mb-16">
        <button
          class="inline-flex items-center px-6 py-3 text-sm text-white border border-white/30 rounded-full hover:bg-white/10 transition-all duration-300">
          <span class="mr-2">→</span>
          Explore company
        </button>
      </div>

      <!-- Main heading -->
      <div class="text-right mb-20">
        <h1 class="text-5xl md:text-6xl lg:text-7xl text-white">
          Join us on a journey to<br>
          <span class="bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
            unlock your digital potential
          </span>
        </h1>
      </div>

      <!-- Cards container -->
      <div class="grid md:grid-cols-3 gap-8 max-w-7xl mx-auto">
        <!-- Mission Card -->
        <div class="group relative h-full">
          <div
            class="relative bg-gradient-to-b from-[#ffffff00] via-purple-900/5 to-purple-900/40 backdrop-blur-lg border border-white/10 rounded-3xl p-8 hover:border-white/20 transition-all duration-500 h-full flex flex-col justify-between gap-10">
            <div class="mb-6">
              <span class="text-slateBlue text-sm font-medium">01.</span>
            </div>

            <h3 class="text-2xl text-white mb-4">Our Mission</h3>

            <p class="text-gray-300 mb-8 leading-relaxed">
              To empower businesses with innovative and strategic technology solutions that foster growth and enhance
              digital presence.
            </p>

            <ThemeBtn :white-bg="false" :white-text="true" :to="'/contact'" :small="true" class="w-full" />

          </div>
        </div>

        <!-- Vision Card -->
        <div class="group relative h-full">
          <div
            class="relative bg-gradient-to-b from-[#ffffff00] via-green-900/5 to-green-900/40 backdrop-blur-lg border border-white/10 rounded-3xl p-8 hover:border-white/20 transition-all duration-500 h-full flex flex-col justify-between gap-10">
            <div class="mb-6">
              <span class="text-slateBlue text-sm font-medium">02.</span>
            </div>

            <h3 class="text-2xl text-white mb-4">Our Vision</h3>

            <p class="text-gray-300 mb-8 leading-relaxed">
              To be a leading force in the digital transformation landscape, recognized for our creativity, expertise,
              and unwavering commitment to client success.
            </p>

            <ThemeBtn :white-bg="false" :white-text="true" :to="'/contact'" :small="true" class="w-full" />

          </div>
        </div>

        <!-- Core Values Card -->
        <div class="group relative h-full">
          <div
            class="relative bg-gradient-to-b from-[#ffffff00] via-blue-900/5 to-blue-900/40 backdrop-blur-lg border border-white/10 rounded-3xl p-8 hover:border-white/20 transition-all duration-500 h-full flex flex-col justify-between gap-10">
            <div class="mb-6">
              <span class="text-slateBlue text-sm font-medium">03.</span>
            </div>

            <h3 class="text-2xl text-white mb-4">Core Values</h3>

            <p class="text-gray-300 mb-8 leading-relaxed">
              Innovation, Collaboration, Excellence, Integrity, Client-Centricity.
            </p>

            <ThemeBtn :white-bg="false" :white-text="true" :to="'/contact'" :small="true" class="w-full" />

          </div>
        </div>
      </div>
    </div>

    <!-- Bottom decorative wave or curve -->
    <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-white/5 to-transparent" />
  </section>
</template>

<script setup>
// You can add any reactive data or methods here if needed
</script>

<style scoped>
/* Additional custom styles if needed */
.bg-clip-text {
  -webkit-background-clip: text;
  background-clip: text;
}
</style>