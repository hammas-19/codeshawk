<template>
  <div class="bg-antiFlash overflow-hidden">
    <HeroBanner :breadcrumbs="[
      { label: 'Home', href: '/' },
      { label: 'Services', href: '/services' }
    ]" :show-cta="true" cta-text="Get Started" cta-link="/contact" :title="'Our Services'" :subtitle="''" :background-image="'https://images.unsplash.com/photo-1711831521065-e546a5aca68e?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'" />
    <ServicesGallery />
    <ServicesChooseUs class="md:mb-[92px] mb-16" />
  </div>
</template>
