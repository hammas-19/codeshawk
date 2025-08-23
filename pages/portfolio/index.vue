<template>
  <div>
    <HeroBanner :breadcrumbs="[
      { label: 'Home', href: '/' },
      { label: 'Portfolio', href: '/portfolio' }
    ]" :show-cta="true" cta-text="Get Started" cta-link="/contact" :title="'Our Portfolio'" :subtitle="''"
      :background-image="'https://images.unsplash.com/photo-1668852222395-11d9154ade25?q=80&w=1972&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'" />
    <PortfolioGallery />
  </div>
</template>