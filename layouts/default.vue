<template>
  <div class="app md:py-6 md:px-4">
    <nuxt />
  </div>
</template>

<script></script>

<style>
@keyframes Gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
.app {
  /* background: linear-gradient(
    -45deg,
    theme('colors.brandOrange'),
    theme('colors.brandBlue'),
    theme('colors.brandPink'),
    theme('colors.brandYellow')
  );
  background-size: 400% 400%;
  animation: Gradient 15s ease infinite; */
  /* background: linear-gradient(theme('colors.brandGreen'), white); */
  background-color: #222;
}
</style>
