<template>
  <section class="md:py-16 pb-5 md:pb-10 px-4 sm:px-6 lg:px-8">
    <div class="grid lg:grid-cols-2 mx-auto md:gap-10 gap-5">
      <div v-for="(project) in props.projects" :key="project.id">
        <div class="w-full relative">
          <!-- Gradient Background -->
          <div class="w-full h-full absolute inset-0 md:rounded-[30px] rounded-[18px]" :style="{
            background: `linear-gradient(135deg, ${project.bgColor}33, ${project.bgColor}44, ${project.bgColor}55)`,
          }" />

          <!-- Main Card -->
          <div
            class="border-2 md:rounded-[30px] rounded-[18px] border-black w-full bg-white hover:bg-transparent backdrop-blur-sm overflow-hidden transition-all duration-300 hover:scale-105 cursor-pointer"
            :style="{ borderColor: project.bgColor }">

            <!-- Header Section -->
            <div class="md:py-10 py-6 md:px-8 px-4">
              <div class="flex justify-between items-center">
                <div class="flex items-center gap-6">
                  <img :src="project.logo" :alt="project.title" class="h-12 w-12 object-cover rounded-xl">
                  <h3 class="text-gray-900 font-bold md:text-4xl sm:text-2xl text-lg uppercase">
                    {{ project.title }}
                  </h3>
                </div>

                <!-- Arrow Button -->
                <button
                  class="group relative flex size-10 items-center justify-center gap-1 rounded-lg w-full max-w-[40px] hover:bg-gray-100 transition-colors duration-200">
                  <div class="size-1 rounded-full bg-black duration-300 group-hover:opacity-0" />
                  <div
                    class="relative size-1 origin-center rounded-full bg-black duration-300 before:absolute before:right-[2px] before:h-1 before:origin-right before:rounded-full before:bg-black before:delay-300 before:duration-300 after:absolute after:right-[2px] after:h-1 after:origin-right after:rounded-full after:bg-black after:delay-300 after:duration-300 group-hover:w-6 group-hover:before:w-3.5 group-hover:before:-rotate-45 group-hover:after:w-3.5 group-hover:after:rotate-45" />
                  <div class="size-1 rounded-full bg-black duration-300 group-hover:opacity-0" />
                </button>
              </div>
            </div>

            <!-- Folder Design -->
            <div class="flex flex-col md:rounded-[18px] rounded-[10px] overflow-hidden w-full">
              <!-- Folder Tab -->
              <div class="flex w-[45%] md:w-[30%] min-h-[40px]">
                <div class="w-3/2 min-h-full mb-[-1px] rounded-tr-sm" :style="{ backgroundColor: project.bgColor }" />
                <div class="theCurve w-[70px] min-h-full md:ml-[-2px] ml-[-2px] mb-[-1px]"
                  :style="{ backgroundColor: project.bgColor }" />
              </div>

              <!-- Main Content Area -->
              <div
                class="md:min-h-[260px] md:rounded-tr-[18px] rounded-tr-[10px] flex flex-col justify-between md:p-6 p-4 sm:gap-8 gap-5"
                :style="{ backgroundColor: project.bgColor }">
                <div class="flex-1">
                  <p class="text-white sm:text-xl text-sm line-clamp-3 leading-relaxed">
                    {{ project.description }}
                  </p>
                </div>

                <!-- Technology Icons -->
                <div class="flex flex-wrap gap-3">
                  <div v-for="tech in project.technologies" :key="tech.name"
                    class="bg-white/10 md:p-3 p-2 rounded-2xl flex justify-center items-center backdrop-blur-sm">
                    <span class="md:text-2xl text-lg">{{ tech.icon }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const props = defineProps({
  projects: {
    type: Array,
    default: () => [
      {
        id: 1,
        title: "E-Commerce Platform",
        description: "A modern e-commerce solution built with cutting-edge technologies, featuring real-time inventory management, secure payment processing, and an intuitive user interface that drives conversions.",
        bgColor: "#636EDF",
        logo: "https://images.unsplash.com/photo-1611224923853-80b023f02d71?q=80&w=100&auto=format&fit=crop",
        technologies: [
          { name: "Vue.js", icon: "🟢" },
          { name: "Node.js", icon: "📗" },
          { name: "MongoDB", icon: "🍃" },
          { name: "Stripe", icon: "💳" }
        ]
      },
      {
        id: 2,
        title: "Brand Identity System",
        description: "Complete visual identity redesign for a tech startup, including logo design, brand guidelines, marketing materials, and digital asset optimization across all platforms.",
        bgColor: "#6b1e3f",
        logo: "https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?q=80&w=100&auto=format&fit=crop",
        technologies: [
          { name: "Figma", icon: "🎨" },
          { name: "Illustrator", icon: "✏️" },
          { name: "Photoshop", icon: "🖼️" },
          { name: "InDesign", icon: "📄" }
        ]
      },
      {
        id: 3,
        title: "Marketing Automation",
        description: "Comprehensive marketing automation suite that streamlines campaign management, customer segmentation, and performance analytics to boost engagement and ROI.",
        bgColor: "#4a5d3a",
        logo: "https://images.unsplash.com/photo-1572021335469-31706a17aaef?q=80&w=100&auto=format&fit=crop",
        technologies: [
          { name: "React", icon: "⚛️" },
          { name: "Python", icon: "🐍" },
          { name: "PostgreSQL", icon: "🐘" },
          { name: "Redis", icon: "🔴" }
        ]
      },
      {
        id: 4,
        title: "Mobile Health App",
        description: "Cross-platform mobile application for health tracking and telemedicine consultations, featuring AI-powered symptom analysis and secure patient data management.",
        bgColor: "#2d4a3e",
        logo: "https://images.unsplash.com/photo-1576091160399-112ba8d25d1f?q=80&w=100&auto=format&fit=crop",
        technologies: [
          { name: "Flutter", icon: "📱" },
          { name: "Firebase", icon: "🔥" },
          { name: "TensorFlow", icon: "🧠" },
          { name: "WebRTC", icon: "📹" }
        ]
      },
      {
        id: 5,
        title: "Data Visualization Dashboard",
        description: "Interactive business intelligence dashboard that transforms complex data into actionable insights through dynamic charts, real-time updates, and customizable reporting.",
        bgColor: "#1e3a8a",
        logo: "https://images.unsplash.com/photo-1551288049-bebda4e38f71?q=80&w=100&auto=format&fit=crop",
        technologies: [
          { name: "D3.js", icon: "📊" },
          { name: "TypeScript", icon: "📘" },
          { name: "Express", icon: "🚀" },
          { name: "Docker", icon: "🐳" }
        ]
      },
      {
        id: 6,
        title: "Content Management System",
        description: "Headless CMS solution designed for content creators and developers, offering flexible content modeling, API-first architecture, and seamless third-party integrations.",
        bgColor: "#7c2d12",
        logo: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?q=80&w=100&auto=format&fit=crop",
        technologies: [
          { name: "Next.js", icon: "▲" },
          { name: "GraphQL", icon: "◉" },
          { name: "Prisma", icon: "🔷" },
          { name: "AWS", icon: "☁️" }
        ]
      }
    ]
  }
})
</script>

<style scoped>
.theCurve {
  clip-path: polygon(0 0, 0 0, 100% 100%, 0% 100%);
}
</style>