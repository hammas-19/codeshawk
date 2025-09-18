<template>
  <section class="py-20 lg:py-32 px-4 sm:px-6 lg:px-8 relative overflow-hidden">
    <img src="/Hero/cylinder.webp" class="absolute md:top-1/5 top-2/3 right-1/8 lg:h-40 w-fit md:h-20 h-16" alt=""
      :style="{
        transition: `all ${bounceEase}`,
        transform: polyElementVisible ?
          'translateX(0) translateY(0) rotate(0deg) scale(1)' :
          'translateX(-100px) translateY(100px) rotate(180deg) scale(0)',
        opacity: polyElementVisible ? 1 : 0
      }" @mouseenter="onHover" @mouseleave="onLeave" @click="triggerPolyElementAnimation">
    <!-- Large Background Text -->
    <div class="absolute inset-0 flex items-center justify-center pointer-events-none">
      <h1
        class="text-[4rem] sm:text-[7rem] lg:text-[10rem] xl:text-[16rem] font-bold text-white/60 select-none leading-none">
        testimonials
      </h1>
    </div>

    <div class="max-w-4xl mx-auto relative z-10 text-center">
      <!-- Badge -->
      <div
        class="inline-flex items-center px-4 py-2 bg-white rounded-full text-sm font-medium text-gray-900 mb-12 shadow-sm border">
        <span class="w-2 h-2 bg-slateBlue rounded-full mr-2"></span>
        Hear from customer
      </div>

      <!-- Testimonials Slider -->
      <div class="keen-slider" ref="container">
        <div v-for="(testimonial, index) in testimonials" :key="index" class="keen-slider__slide">
          <div class="text-center">
            <!-- Quote -->
            <blockquote
              class="text-3xl sm:text-4xl lg:text-5xl font-medium text-gray-900 leading-tight mb-12 max-w-4xl mx-auto">
              "{{ testimonial.quote }}"
            </blockquote>

            <!-- Author Info -->
            <div class="space-y-1">
              <p class="text-lg font-semibold text-slateBlue">
                {{ testimonial.name }}
              </p>
              <p class="text-gray-900">
                {{ testimonial.position }}
              </p>
            </div>
          </div>
        </div>
      </div>

      <!-- Navigation Dots -->
      <div class="flex justify-center mt-12 space-x-3">
        <button v-for="(dot, idx) in testimonials" :key="idx" @click="goToSlide(idx)"
          class="w-3 h-3 rounded-full transition-all duration-300"
          :class="currentSlide === idx ? 'bg-slateBlue' : 'bg-gray-300'" />
      </div>
    </div>
  </section>
</template>

<script setup>
import { spring } from 'motion-v'

// Testimonials data
const testimonials = ref([
  {
    quote: "Their fresh perspective and innovative strategies have given our business a much-needed revamp.",
    name: "Anna Perry",
    position: "Director of Recon"
  },
  {
    quote: "The team's dedication and expertise transformed our digital presence beyond our expectations.",
    name: "Michael Johnson",
    position: "CEO, Innovation Labs"
  },
  {
    quote: "Outstanding service and remarkable results. They truly understand what modern businesses need.",
    name: "Sarah Williams",
    position: "Marketing Director"
  },
  {
    quote: "Professional, reliable, and incredibly talented. Working with them was a game-changer for us.",
    name: "David Chen",
    position: "Founder, StartupHub"
  }
]);

// Slider state
const currentSlide = ref(0);

// Initialize keen slider - 1 slide per view only
const [container, slider] = useKeenSlider({
  initial: 0,
  loop: true,
  mode: "snap",
  slides: {
    perView: 1,
    spacing: 0,
  },
  slideChanged: (s) => {
    if (s && s.track && s.track.details) {
      currentSlide.value = s.track.details.rel;
    }
  },
});

// Navigation methods
const goToSlide = (index) => {
  if (slider.value) {
    slider.value.moveToIdx(index);
  }
};

// Auto-play functionality
let autoPlayInterval = null;

const startAutoPlay = () => {
  if (slider.value) {
    autoPlayInterval = setInterval(() => {
      if (slider.value) {
        slider.value.next();
      }
    }, 5000);
  }
};

const stopAutoPlay = () => {
  if (autoPlayInterval) {
    clearInterval(autoPlayInterval);
    autoPlayInterval = null;
  }
};
const polyElementVisible = ref(false)
const isHovered = ref(false)

// Spring easing for smooth bouncy animation
const bounceEase = spring(0.6, 0.7)
const hoverEase = spring(0.8, 0.9)

// Interactive handlers (same for both images)
const onHover = (event) => {
  isHovered.value = true

  // Get element and cursor positions
  const rect = event.target.getBoundingClientRect()
  const elementCenterX = rect.left + rect.width / 2
  const elementCenterY = rect.top + rect.height / 2
  const cursorX = event.clientX
  const cursorY = event.clientY

  // Calculate direction from cursor to element center
  const deltaX = elementCenterX - cursorX
  const deltaY = elementCenterY - cursorY

  // Normalize and scale the movement (move away from cursor)
  const distance = Math.sqrt(deltaX * deltaX + deltaY * deltaY)
  const moveDistance = 30 // How far to move away
  const moveX = (deltaX / distance) * moveDistance
  const moveY = (deltaY / distance) * moveDistance

  event.target.style.transition = `transform ${hoverEase}`
  event.target.style.transform = `translateX(${moveX}px) translateY(${moveY}px) rotate(15deg) scale(1.05)`
}

const onLeave = (event) => {
  isHovered.value = false
  event.target.style.transition = `transform ${bounceEase}`
  event.target.style.transform = 'translateX(0) translateY(0) rotate(0deg) scale(1)'
}


const triggerPolyElementAnimation = () => {
  console.log('Poly element clicked!')
  polyElementVisible.value = false
  setTimeout(() => {
    polyElementVisible.value = true
  }, 300)
}
// Lifecycle
onMounted(() => {
  setTimeout(() => {
    polyElementVisible.value = true
  }, 1200)
  nextTick(() => {
    startAutoPlay();
  });
});

onUnmounted(() => {
  stopAutoPlay();
});
</script>

<style scoped>
.keen-slider__slide {
  min-height: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>