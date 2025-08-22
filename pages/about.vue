<template>
  <div class=" bg-antiFlash">
    <HeroBanner :breadcrumbs="[
      { label: 'Home', href: '/' },
      { label: 'About Us', href: '/about' }
    ]" :show-cta="true" cta-text="Get Started" cta-link="/contact" />
    <AboutStory @cta-clicked="handleBrochureDownload" />
    <AboutJourney />
    <TheTestimonials class="md:py-[92px] py-16" />
    <!-- <MotionTest /> -->
  </div>
</template>
<script setup>
const handleBrochureDownload = () => {
  // Simple file download
  const link = document.createElement('a')
  link.href = 'assets/blahblah.pdf'
  link.download = 'CodesHawk-Company-Brochure.pdf'
  link.click()
}
</script>