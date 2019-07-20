<template>
  <header
    class="min-height w-full flex mb-4 md:px-2"
    :class="!wide && 'lg:w-2/3 xl:w-1/2'"
  >
    <div class="min-w-full bg-brandYellow text-white p-4">
      <h1 class="text-6xl">
        <n-link to="/">{{ header.greeting }}</n-link>
      </h1>
      <p class="text-brandDBlue">
        {{ header.subtitle }}
      </p>
      <p>SOCIAL</p>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    wide: {
      type: Boolean
    }
    // header: {
    //   type: Object,
    //   required: true,
    //   greeting: {
    //     type: String,
    //     required: true
    //   }
    // }
    // greeting: {
    //   type: String,
    //   required: true
    // },
    // subtitle: {
    //   type: String,
    //   required: true
    // }
  },
  computed: {
    header() {
      return this.$store.state.header
    }
  }
}
</script>

<style>
header {
  position: relative;
  z-index: 2;
  min-height: 275px;
}

@media (min-width: 1480px) {
  header::before {
    content: '';
    display: block;
    position: absolute;
    top: 0;
    right: 100%;
    bottom: 0;
    left: -99999em;
    transform: translateX(0.5rem);
    background-color: theme('colors.brandYellow');
    background-image: url(~assets/images/hello.svg);
    background-position: top right;
    background-repeat: no-repeat;
    z-index: -1;
  }
}
</style>
