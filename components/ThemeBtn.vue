<template>
  <button
    class="learn-more relative inline-block cursor-pointer outline-none border-2 align-middle no-underline bg-transparent p-1.5 text-inherit font-inherit w-52 h-auto rounded-2xl items-center mt-2">
    <span class="circle learn-more-transition relative block m-0 w-12 h-12 bg-slateBlue rounded-2xl" aria-hidden="true">
      <span class="learn-more-transition absolute top-0 bottom-0 my-auto  w-full  h-full bg-none flex justify-center items-center">
        <Icon name="hugeicons:circle-arrow-up-right" class="min-h-8 min-w-8" />
      </span>
    </span>
    <span
      class="button-text learn-more-transition absolute top-0 left-0 right-0 bottom-0 py-3 px-0 ml-7 text-gray-800 font-bold leading-relaxed text-center uppercase">Learn
      More</span>
  </button>
</template>

<style scoped>
/* Custom animations and pseudo-elements that aren't possible with pure Tailwind */
.learn-more-transition {
  transition: all 0.45s cubic-bezier(0.65, 0, 0.076, 1);
}

.arrow-icon::before {
  content: "";
  position: absolute;
  top: -0.29rem;
  right: 0.0625rem;
  width: 0.625rem;
  height: 0.625rem;
  border-top: 0.125rem solid #fff;
  border-right: 0.125rem solid #fff;
  transform: rotate(45deg);
}

.learn-more:hover .circle {
  width: 100%;
}

.learn-more:hover .arrow-icon {
  background: #fff;
  /* transform: translate(1rem, 0); */
}

.learn-more:hover .button-text {
  color: #fff;
}
</style>