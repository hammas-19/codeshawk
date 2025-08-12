<template>
  <div class="bg-gray-50 min-h-screen py-16">
    <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header Section -->
      <div class="text-center mb-12">
        <div class="flex items-center justify-center mb-6">
          <div class="w-2 h-2 bg-blue-500 rounded-full mr-3"></div>
          <span class="text-sm text-gray-600 uppercase tracking-wide">Get in touch</span>
        </div>
        <h1 class="text-5xl md:text-6xl font-bold text-gray-900 leading-tight">
          We're ready to<br>
          help you!
        </h1>
      </div>

      <!-- Contact Form -->
      <div class="max-w-2xl mx-auto mb-20">
        <form @submit.prevent="submitForm" class="space-y-6">
          <!-- Name Fields Row -->
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div>
              <input v-model="form.firstName" type="text" placeholder="First Name"
                class="w-full px-6 py-4 bg-white rounded-xl border border-gray-200 focus:border-blue-500 focus:ring-2 focus:ring-blue-200 outline-none transition-all text-gray-900 placeholder-gray-500"
                required>
            </div>
            <div>
              <input v-model="form.lastName" type="text" placeholder="Last Name"
                class="w-full px-6 py-4 bg-white rounded-xl border border-gray-200 focus:border-blue-500 focus:ring-2 focus:ring-blue-200 outline-none transition-all text-gray-900 placeholder-gray-500"
                required>
            </div>
          </div>

          <!-- Email Field -->
          <div>
            <input v-model="form.email" type="email" placeholder="Your Email"
              class="w-full px-6 py-4 bg-white rounded-xl border border-gray-200 focus:border-blue-500 focus:ring-2 focus:ring-blue-200 outline-none transition-all text-gray-900 placeholder-gray-500"
              required>
          </div>

          <!-- Contact Number Field -->
          <div>
            <input v-model="form.contactNumber" type="tel" placeholder="Contact Number"
              class="w-full px-6 py-4 bg-white rounded-xl border border-gray-200 focus:border-blue-500 focus:ring-2 focus:ring-blue-200 outline-none transition-all text-gray-900 placeholder-gray-500">
          </div>

          <!-- Website Field -->
          <div>
            <input v-model="form.website" type="url" placeholder="Website (Optional)"
              class="w-full px-6 py-4 bg-white rounded-xl border border-gray-200 focus:border-blue-500 focus:ring-2 focus:ring-blue-200 outline-none transition-all text-gray-900 placeholder-gray-500">
          </div>

          <!-- Message Field -->
          <div>
            <textarea v-model="form.message" placeholder="Your Message" rows="6"
              class="w-full px-6 py-4 bg-white rounded-xl border border-gray-200 focus:border-blue-500 focus:ring-2 focus:ring-blue-200 outline-none transition-all resize-none text-gray-900 placeholder-gray-500"
              required></textarea>
          </div>

          <!-- Swipe to Submit Button -->
          <div class="relative">
            <motion.div class="relative w-full h-[70px] rounded-[35px] overflow-hidden transition-all duration-300"
              :class="{ 'opacity-50 cursor-not-allowed': !isFormValid || isSubmitting, 'cursor-grab': isFormValid && !isSubmitting }"
              :style="{ background: swipeBackground }">
              <!-- Background Text -->
              <div class="absolute inset-0 flex items-center justify-center text-white font-semibold text-lg z-10">
                <span v-if="!isSubmitting">{{ swipeText }}</span>
                <span v-else class="flex items-center justify-center">
                  <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none"
                    viewBox="0 0 24 24">
                    <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                    <path class="opacity-75" fill="currentColor"
                      d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z">
                    </path>
                  </svg>
                  Sending...
                </span>
              </div>

              <!-- Draggable Button -->
              <motion.div
                class="absolute left-[5px] top-[5px] w-[60px] h-[60px] bg-white rounded-full flex items-center justify-center z-20 shadow-lg cursor-grab active:cursor-grabbing"
                :style="{ x: swipeX }" drag="x" :drag-constraints="{ left: 0, right: maxDragDistance }"
                :drag-elastic="0.1" @drag="handleDrag" @drag-end="handleDragEnd" v-if="!isSubmitting && isFormValid">
                <!-- Icon inside button -->
                <Icon name="iconoir:send" class="text-green-600 min-h-10 min-w-10" />
              </motion.div>
            </motion.div>
          </div>
        </form>
      </div>

      <!-- Offices Section -->
      <div class="border-t border-gray-300 pt-16">
        <div class="mb-8">
          <div class="flex items-center mb-6">
            <div class="w-2 h-2 bg-gray-400 rounded-full mr-3"></div>
            <span class="text-sm text-gray-600 uppercase tracking-wide">Our offices</span>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-12">
          <!-- Las Vegas Office -->
          <div class="text-left">
            <h3 class="text-2xl font-bold text-gray-900 mb-4">
              Las Vegas,<br>
              United States
            </h3>
            <div class="text-gray-600 space-y-1">
              <p>82 W. Wild Horse Drive</p>
              <p>Warren, MI 48089</p>
            </div>
          </div>

          <!-- Buenos Aires Office -->
          <div class="text-left">
            <h3 class="text-2xl font-bold text-gray-900 mb-4">
              Buenos Aires<br>
              Argentina
            </h3>
            <div class="text-gray-600 space-y-1">
              <p>8605 Sugar Ave, Sugar Land,</p>
              <p>TX 77478</p>
            </div>
          </div>

          <!-- Montevideo Office -->
          <div class="text-left">
            <h3 class="text-2xl font-bold text-gray-900 mb-4">
              Montevideo,<br>
              Uruguay
            </h3>
            <div class="text-gray-600 space-y-1">
              <p>7757 El Dorado Ave.</p>
              <p>Libertyville, IL 60048</p>
            </div>
          </div>
        </div>
      </div>

    </div>

    <!-- Response Dialog Modal -->
    <div v-if="showDialog"
      class="fixed inset-0 bg-[#403f3f58] backdrop-blur-lg bg-opacity-50 flex items-center justify-center z-50 p-4">
      <div class="bg-white rounded-2xl p-8 max-w-md w-full mx-4 transform transition-all duration-300 scale-100">
        <div class="text-center">
          <!-- Success Icon -->
          <div v-if="dialogType === 'success'"
            class="mx-auto flex items-center justify-center h-16 w-16 rounded-full bg-green-100 mb-4">
            <Icon name="hugeicons:sent-02" class="text-green-600 min-h-10 min-w-10" />
          </div>

          <!-- Error Icon -->
          <div v-else class="mx-auto flex items-center justify-center h-16 w-16 rounded-full bg-red-100 mb-4">
            <svg class="h-8 w-8 text-red-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
            </svg>
          </div>

          <!-- Title -->
          <h3 class="text-xl font-bold text-gray-900 mb-3">
            {{ dialogType === 'success' ? 'Message Sent!' : 'Oops! Something went wrong' }}
          </h3>

          <!-- Message -->
          <p class="text-gray-600 mb-6 leading-relaxed">
            {{ dialogMessage }}
          </p>

          <!-- Close Button -->
          <button @click="closeDialog"
            :class="dialogType === 'success' ? 'bg-green-600 hover:bg-green-700' : 'bg-red-600 hover:bg-red-700'"
            class="w-full text-white py-3 px-6 rounded-xl font-semibold transition-colors">
            {{ dialogType === 'success' ? 'Great!' : 'Try Again' }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useMotionValue, useTransform, motion } from 'motion-v'

// Form reactive data
const form = ref({
  firstName: '',
  lastName: '',
  email: '',
  contactNumber: '',
  website: '',
  message: ''
})

const isSubmitting = ref(false)
const showDialog = ref(false)
const dialogMessage = ref('')
const dialogType = ref('success')

// Swipe motion values
const swipeX = useMotionValue(0)
const maxDragDistance = 300 // Maximum swipe distance
const swipeProgress = ref(0)

// Transform values for swipe effect
const swipeBackground = useTransform(
  swipeX,
  [0, maxDragDistance],
  [
    "linear-gradient(90deg, #3b82f6 0%, #1d4ed8 100%)",
    "linear-gradient(90deg, #10b981 0%, #059669 100%)"
  ]
)


// Computed text based on swipe progress
const swipeText = computed(() => {
  if (swipeProgress.value < 0.3) return "Swipe to Send Message"
  if (swipeProgress.value < 0.7) return "Keep Swiping..."
  if (swipeProgress.value < 0.9) return "Almost There!"
  return "Release to Send!"
})

// Handle drag movement
const handleDrag = (event, info) => {
  const progress = Math.min(info.point.x / maxDragDistance, 1)
  swipeProgress.value = Math.max(0, progress)
}

// Handle drag end
const handleDragEnd = (event, info) => {
  const progress = info.point.x / maxDragDistance

  if (progress >= 0.9 && isFormValid.value && !isSubmitting.value) {
    // Trigger form submission
    submitForm()
  } else {
    // Snap back to start
    swipeX.set(0)
    swipeProgress.value = 0
  }
}

// Reset swipe position after submission
const resetSwipe = () => {
  swipeX.set(0)
  swipeProgress.value = 0
}

// Submit form handler
const submitForm = async () => {
  isSubmitting.value = true

  try {
    const formData = new FormData()
    formData.append('access_key', 'f92c1a2b-eedc-4f5e-a4c6-ec8004859448')
    formData.append('name', `${form.value.firstName} ${form.value.lastName}`)
    formData.append('email', form.value.email)
    formData.append('phone', form.value.contactNumber || '')
    formData.append('website', form.value.website || '')
    formData.append('message', form.value.message)
    formData.append('subject', `New Contact Form Submission from ${form.value.firstName}`)
    formData.append('from_name', `${form.value.firstName} ${form.value.lastName}`)
    formData.append('replyto', form.value.email)

    const response = await fetch('https://api.web3forms.com/submit', {
      method: 'POST',
      body: formData
    })

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`)
    }

    const data = await response.json()

    if (data.success) {
      dialogType.value = 'success'
      dialogMessage.value = 'Thank you! Your message has been sent successfully. We\'ll get back to you soon.'
      showDialog.value = true

      // Reset form after successful submission
      form.value = {
        firstName: '',
        lastName: '',
        email: '',
        contactNumber: '',
        website: '',
        message: ''
      }
      resetSwipe()
    } else {
      throw new Error(data.message || 'Form submission failed')
    }

  } catch (error) {
    console.error('Form submission error:', error)
    dialogType.value = 'error'
    dialogMessage.value = `Error: ${error.message}. Please try again or contact us directly.`
    showDialog.value = true
    resetSwipe()
  } finally {
    isSubmitting.value = false
  }
}

// Close dialog
const closeDialog = () => {
  showDialog.value = false
  dialogMessage.value = ''
}

// Form validation
const isFormValid = computed(() => {
  return form.value.firstName &&
    form.value.lastName &&
    form.value.email &&
    form.value.message
})

// SEO Meta
useHead({
  title: 'Contact Us - Get in Touch',
  meta: [
    { name: 'description', content: 'Ready to help you! Contact our team through our offices in Las Vegas, Buenos Aires, and Montevideo.' }
  ]
})
</script>

<style scoped>
/* Only keep essential styles that Tailwind can't handle */
input:focus,
textarea:focus {
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

/* Responsive mobile adjustments */
@media (max-width: 768px) {
  .swipe-container-mobile {
    height: 60px !important;
    border-radius: 30px !important;
  }

  .swipe-button-mobile {
    width: 50px !important;
    height: 50px !important;
  }
}
</style>