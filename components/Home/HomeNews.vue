<template>
  <div class="bg-gray-50 min-h-screen py-12">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Header Section -->
      <div class="mb-8">
        <div class="flex items-center mb-6">
          <div class="w-2 h-2 bg-gray-400 rounded-full mr-3"></div>
          <span class="text-sm text-gray-500 uppercase tracking-wide">Recent post</span>
        </div>
        <h1 class="text-4xl md:text-5xl font-bold text-gray-900 leading-tight">
          Latest news and<br>
          industry insights
        </h1>
      </div>

      <!-- Featured Article Card -->
      <div class="mb-8" v-if="featuredArticle">
        <div class="bg-white rounded-2xl overflow-hidden shadow-sm border border-gray-100 relative">
          <!-- Featured Image -->
          <div class="relative h-80">
            <img :src="featuredArticle.image" :alt="featuredArticle.title" class="w-full h-full object-cover">
          </div>

          <!-- Content Section -->
          <div class="p-8 relative">
            <!-- Arrow Button - positioned absolute in top right -->
            <button @click="readArticle(featuredArticle.id)"
              class="absolute top-6 right-6 bg-blue-600 text-white w-12 h-12 rounded-full flex items-center justify-center hover:bg-blue-700 transition-colors">
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
              </svg>
            </button>

            <!-- Meta Information -->
            <div class="flex items-center space-x-4 text-xs text-gray-500 mb-4 uppercase tracking-wide">
              <span :class="getCategoryClasses(featuredArticle.category)" class="px-2 py-1 rounded-full font-medium">
                {{ featuredArticle.category }}
              </span>
              <span>{{ featuredArticle.date }}</span>
              <span>{{ featuredArticle.author }}</span>
            </div>

            <!-- Title -->
            <h2 class="text-3xl font-bold text-gray-900 mb-4 pr-16">
              {{ featuredArticle.title }}
            </h2>

            <!-- Excerpt -->
            <p class="text-gray-600 leading-relaxed pr-16">
              {{ featuredArticle.excerpt }}
            </p>
          </div>
        </div>
      </div>

      <!-- Articles List -->
      <div class="space-y-4">
        <article v-for="article in regularArticles" :key="article.id"
          class="bg-white rounded-xl overflow-hidden shadow-sm border border-gray-100 hover:shadow-md transition-shadow cursor-pointer"
          @click="readArticle(article.id)">
          <div class="flex">
            <!-- Article Image -->
            <div class="w-48 h-32 flex-shrink-0">
              <img :src="article.image" :alt="article.title" class="w-full h-full object-cover">
            </div>

            <!-- Article Content -->
            <div class="flex-1 p-6 flex flex-col justify-center">
              <!-- Meta Information -->
              <div class="flex items-center space-x-4 text-xs text-gray-500 mb-3 uppercase tracking-wide">
                <span :class="getCategoryClasses(article.category)" class="px-2 py-1 rounded-full font-medium">
                  {{ article.category }}
                </span>
                <span>{{ article.date }}</span>
                <span>{{ article.author }}</span>
              </div>

              <!-- Title -->
              <h3 class="text-xl font-bold text-gray-900 leading-tight">
                {{ article.title }}
              </h3>
            </div>
          </div>
        </article>
      </div>

      <!-- Decorative 3D Element -->
      <div class="fixed bottom-8 left-8 w-20 h-20 opacity-30">
        <div class="relative w-full h-full">
          <div
            class="absolute inset-0 bg-gradient-to-br from-purple-400 to-pink-400 rounded-2xl transform rotate-12 shadow-lg">
          </div>
          <div
            class="absolute inset-0 bg-gradient-to-tl from-purple-500 to-blue-500 rounded-2xl transform rotate-6 shadow-lg opacity-80">
          </div>
          <div
            class="absolute inset-0 bg-gradient-to-r from-blue-400 to-purple-400 rounded-2xl transform -rotate-3 shadow-lg opacity-60">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// JSON data for articles
const articlesData = ref([
  {
    id: 1,
    title: "Top Digital Agency Case Studies in Web3 Marketing",
    category: "Company",
    date: "29 NOV 2024",
    author: "ADMIN",
    excerpt: "We bring deep, functional expertise, but are known for our holistic perspective: we capture value across boundaries...",
    image: "https://images.unsplash.com/photo-1522202176988-66273c2fd55f?w=800&h=400&fit=crop&crop=faces",
    featured: true,
    slug: "web3-marketing-case-studies"
  },
  {
    id: 2,
    title: "Why Personalization is the Future of Digital Advertising",
    category: "Lifestyle",
    date: "29 NOV 2024",
    author: "ADMIN",
    excerpt: "Discover how personalized marketing strategies are revolutionizing customer engagement and driving higher conversion rates.",
    image: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=400&h=250&fit=crop",
    featured: false,
    slug: "personalization-digital-advertising"
  },
  {
    id: 3,
    title: "Top Crypto Exchange Influencers in Hong Kong",
    category: "Social Media",
    date: "28 NOV 2024",
    author: "ADMIN",
    excerpt: "Meet the leading voices shaping cryptocurrency trading and investment decisions in Hong Kong's dynamic market.",
    image: "https://images.unsplash.com/photo-1559526324-4b87b5e36e44?w=400&h=250&fit=crop",
    featured: false,
    slug: "crypto-influencers-hong-kong"
  },
  {
    id: 4,
    title: "Top UI/UX Design Trends for 2024",
    category: "Lifestyle",
    date: "26 NOV 2024",
    author: "ADMIN",
    excerpt: "Explore the cutting-edge design trends that will define user experiences in 2024 and beyond.",
    image: "https://images.unsplash.com/photo-1581291518857-4e27b48ff24e?w=400&h=250&fit=crop",
    featured: false,
    slug: "ui-ux-design-trends-2024"
  }
])

// Computed properties for data separation
const featuredArticle = computed(() => {
  return articlesData.value.find(article => article.featured)
})

const regularArticles = computed(() => {
  return articlesData.value.filter(article => !article.featured)
})

// Method to get category styling classes
const getCategoryClasses = (category) => {
  const categoryStyles = {
    'Company': 'bg-blue-100 text-blue-600',
    'Lifestyle': 'bg-purple-100 text-purple-600',
    'Social Media': 'bg-green-100 text-green-600',
    'Design': 'bg-orange-100 text-orange-600',
    'Technology': 'bg-red-100 text-red-600',
    'Environment': 'bg-emerald-100 text-emerald-600'
  }
  return categoryStyles[category] || 'bg-gray-100 text-gray-600'
}

// Method to handle article clicks
const readArticle = (articleId) => {
  const article = articlesData.value.find(a => a.id === articleId)
  if (article) {
    console.log('Reading article:', article.title)
    // Example: navigateTo(`/articles/${article.slug}`)
  }
}

// SEO Meta
useHead({
  title: 'Latest News and Industry Insights',
  meta: [
    { name: 'description', content: 'Stay updated with the latest news and insights from the digital marketing and web3 industry.' }
  ]
})
</script>

<style scoped>
/* Custom animations for the 3D decorative element */
@keyframes float3d {

  0%,
  100% {
    transform: translateY(0px) rotateX(10deg) rotateY(10deg);
  }

  50% {
    transform: translateY(-15px) rotateX(15deg) rotateY(15deg);
  }
}

.fixed div div {
  animation: float3d 8s ease-in-out infinite;
}

.fixed div div:nth-child(2) {
  animation-delay: -2s;
}

.fixed div div:nth-child(3) {
  animation-delay: -4s;
}

/* Hover effects */
article:hover {
  transform: translateY(-2px);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .flex {
    flex-direction: column;
  }

  .w-48 {
    width: 100%;
    height: 200px;
  }
}
</style>