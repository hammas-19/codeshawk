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
      <div class="text-center mb-20">
        <h1 class="text-5xl md:text-6xl lg:text-7xl font-bold text-white leading-tight">
          Join us on a journey to<br>
          <span class="bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
            unlock your digital potential
          </span>
        </h1>
      </div>

      <!-- Cards container -->
      <div class="grid md:grid-cols-3 gap-8 max-w-7xl mx-auto">
        <!-- Mission Card -->
        <div class="group relative">
          <div
            class="absolute inset-0 bg-gradient-to-br from-blue-500/20 to-purple-500/20 rounded-3xl blur-xl group-hover:blur-2xl transition-all duration-500" />
          <div
            class="relative bg-gradient-to-br from-blue-900/40 to-purple-900/40 backdrop-blur-lg border border-white/10 rounded-3xl p-8 hover:border-white/20 transition-all duration-500">
            <div class="mb-6">
              <span class="text-blue-400 text-sm font-medium">01.</span>
            </div>

            <h3 class="text-2xl font-bold text-white mb-4">Our Mission</h3>

            <p class="text-gray-300 mb-8 leading-relaxed">
              To empower businesses with innovative and strategic technology solutions that foster growth and enhance
              digital presence.
            </p>

            <button
              class="inline-flex items-center justify-center w-12 h-12 bg-blue-600 hover:bg-blue-700 text-white rounded-full transition-all duration-300 hover:scale-110">
              <span class="text-lg">→</span>
            </button>
            <span class="ml-3 text-white text-sm">Contact Us</span>
          </div>
        </div>

        <!-- Vision Card -->
        <div class="group relative">
          <div
            class="absolute inset-0 bg-gradient-to-br from-purple-500/20 to-pink-500/20 rounded-3xl blur-xl group-hover:blur-2xl transition-all duration-500" />
          <div
            class="relative bg-gradient-to-br from-purple-900/40 to-pink-900/40 backdrop-blur-lg border border-white/10 rounded-3xl p-8 hover:border-white/20 transition-all duration-500">
            <div class="mb-6">
              <span class="text-purple-400 text-sm font-medium">02.</span>
            </div>

            <h3 class="text-2xl font-bold text-white mb-4">Our Vision</h3>

            <p class="text-gray-300 mb-8 leading-relaxed">
              To be a leading force in the digital transformation landscape, recognized for our creativity, expertise,
              and unwavering commitment to client success.
            </p>

            <button
              class="inline-flex items-center justify-center w-12 h-12 bg-purple-600 hover:bg-purple-700 text-white rounded-full transition-all duration-300 hover:scale-110">
              <span class="text-lg">→</span>
            </button>
            <span class="ml-3 text-white text-sm">Our Solutions</span>
          </div>
        </div>

        <!-- Core Values Card -->
        <div class="group relative">
          <div
            class="absolute inset-0 bg-gradient-to-br from-pink-500/20 to-red-500/20 rounded-3xl blur-xl group-hover:blur-2xl transition-all duration-500" />
          <div
            class="relative bg-gradient-to-br from-pink-900/40 to-red-900/40 backdrop-blur-lg border border-white/10 rounded-3xl p-8 hover:border-white/20 transition-all duration-500">
            <div class="mb-6">
              <span class="text-pink-400 text-sm font-medium">03.</span>
            </div>

            <h3 class="text-2xl font-bold text-white mb-4">Core Values</h3>

            <p class="text-gray-300 mb-8 leading-relaxed">
              Innovation, Collaboration, Excellence, Integrity, Client-Centricity.
            </p>

            <button
              class="inline-flex items-center justify-center w-12 h-12 bg-pink-600 hover:bg-pink-700 text-white rounded-full transition-all duration-300 hover:scale-110">
              <span class="text-lg">→</span>
            </button>
            <span class="ml-3 text-white text-sm">Discover More</span>
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