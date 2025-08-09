<template>
  <div class="rounded-2xl">
    <NuxtLink v-if="props.small" :to="props.to"
      class="bg-white text-center w-28 rounded-lg h-10 relative text-black text-xl font-semibold group flex items-center justify-center"
      type="button">
      <div
        class="bg-[#636EDF] rounded-lg h-8 w-1/4 flex items-center justify-center absolute left-1 top-[4px] group-hover:w-28 z-10 duration-500">
        <Icon name="material-symbols:arrow-right-alt-rounded" class="text-white " />
      </div>
      <p class="translate-x-2 ml-4 text-xs text-left">{{ props.text }}</p>
    </NuxtLink>
    <NuxtLink v-else :to="props.to"
      class="bg-white text-center w-48 rounded-2xl h-14 relative text-black text-xl font-semibold group flex items-center justify-center"
      type="button">
      <div
        class="bg-[#636EDF] rounded-xl h-12 w-1/4 flex items-center justify-center absolute left-1 top-[4px] group-hover:w-[184px] z-10 duration-500">
        <Icon name="material-symbols:arrow-right-alt-rounded" class="text-white " />
      </div>
      <p class="translate-x-2 ml-4 text-xs text-left">{{ props.text }}</p>
    </NuxtLink>
  </div>
</template>

<script setup>
// Define props
const props = defineProps({
  text: {
    type: String,
    default: 'Get Started'
  },
  to: {
    type: String,
    required: true
  },
  small: {
    type: Boolean,
    required: false,
    default: false
  }
})
</script>