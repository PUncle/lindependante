<template>
  <footer
    class="min-height w-full flex md:w-1/2 lg:w-1/3 xl:w-1/4 mb-4 md:px-2"
  >
    <div class="min-w-full bg-brandYellow text-white p-4">
      <h1 class="text-6xl">GOODBYE</h1>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
  // props: {
  //   greeting: {
  //     type: String,
  //     required: true
  //   },
  //   subtitle: {
  //     type: String,
  //     required: true
  //   }
  // }
}
</script>

<style>
footer {
  position: relative;
  z-index: 1;
  min-height: 275px;
}

footer::after {
  content: '';
  display: block;
  position: absolute;
  top: 0;
  left: 50%;
  bottom: 0;
  width: 99999em;
  background-color: theme('colors.brandYellow');
  z-index: -1;
}
</style>
