<template>
  <main class="wrapper flex mb-4 flex-wrap justify-start mx-auto">
    <Header :wide="true" />
    <article class="min-height w-full flex mb-4 px-2">
      <div class="min-w-full bg-white text-grey-800 px-4 py-10">
        <!-- eslint-disable-next-line vue/no-v-html -->
        <div class="md:w-3/4 xl:w-1/2 m-auto" v-html="content"></div>
      </div>
    </article>
    <Footer />
  </main>
</template>

<script>
import Header from '~/components/Header'
import Footer from '~/components/Footer'

export default {
  components: {
    Header,
    Footer
  },
  data() {
    return {
      project: this.$store.state.projects.projects.filter(
        project => project.slug === this.$route.params.projectDetail
      )[0]
    }
  },

  async asyncData({ params, error }) {
    try {
      const fileContent = await import(
        `@/static/projects/${params.projectDetail}/${params.projectDetail}.md`
      )
      return {
        content: fileContent.default
      }
    } catch (err) {
      error({
        statusCode: 404,
        message: 'Oh. It seems that you may be lost.'
      })
      // return {
      //   content: `<h2>TUTU! There is no Markdown file found for this project!</h2><p>${err}</p>`
      // }
    }
  }
}
</script>

<style scoped>
article >>> h1 {
  font-size: 4rem;
}

article >>> p {
  margin: 1rem 0 2rem;
}

article >>> ul li {
  list-style-type: disc;
  margin-left: 2rem;
}
</style>
