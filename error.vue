<template>
  <div class="bg-antiFlash">
    <TheNavbar />
    <div class="def-container min-h-[600px] flex flex-col justify-center items-center gap-10 def-padding">
      <img src="/404.webp" alt="Error 404">
      <h1 class="text-black md:text-6xl text-3xl text-center">
        Page Not Found
      </h1>
      <p class="text-darkLiver !text-center">It looks like nothing was found at this location. You can either go <br>
        back to the last page or go to <a href="/" class="text-black font-bold">Home Page</a></p>
      <ThemeBtn :text="'Go to Home'" :to="'/'" />
    </div>
    <TheFooter />
  </div>
</template>