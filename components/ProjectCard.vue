<template>
  <article
    class="min-height w-full flex md:w-1/2 lg:w-1/3 xl:w-1/4 mb-4 md:px-2"
  >
    <n-link :to="slug" class="w-full flex">
      <div class="inner min-w-full min-h-full flex items-stretch">
        <div
          class="img bg-gray-900 min-w-full min-h-full"
          :style="`background-image: url(/projects/${slug}/${thumb})`"
        >
          <div class="copy p-8 min-w-full min-h-full" :class="category">
            <h2 class="mb-3 font-bold">
              {{ title }} <span class="text-white">{{ subtitle }}</span>
            </h2>
            <p>{{ description }}</p>
          </div>
        </div>
      </div>
    </n-link>
  </article>
</template>

<script>
export default {
  name: 'ProjectCard',
  props: {
    title: {
      type: String,
      required: true
    },
    subtitle: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    },
    thumb: {
      type: String,
      required: false,
      default: ''
    },
    category: {
      type: String,
      required: true
    },
    slug: {
      type: String,
      required: true
    }
  },
  computed: {}
}
</script>

<style scoped>
article >>> h2 {
  font-size: 1.6rem;
}

article h2 span {
  font-size: 1.2rem;
  text-transform: lowercase;
  color: rgb(224, 224, 224);
}

article .inner {
  background-color: #333;
}

article .img {
  transition: all 400ms cubic-bezier(0.6, 0.01, 0, 1);
  backface-visibility: hidden;
  background-size: 100%;
  background-position: 50% -100%;
  overflow: hidden;
  background-repeat: no-repeat;
}

article:hover .img {
  background-size: 100%;
  background-position: 50% 50%;
  opacity: 1;
  overflow: hidden;
  transition: all 300ms cubic-bezier(0.6, 0.01, 0, 1);
}

article .copy {
  transform: scale(1);
  transition: all 400ms cubic-bezier(0.55, 0.01, 0.51, 1);
  opacity: 1;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  backface-visibility: hidden;
}

article:hover .copy {
  transform: scale(1.6);
  transition: all 400ms cubic-bezier(0.6, 0.01, 0, 1.28);
  opacity: 0;
}
</style>
