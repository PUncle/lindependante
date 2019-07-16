<template>
  <main class="wrapper flex mb-4 flex-wrap justify-start mx-auto">
    <Header />
    <!-- <h1>{{ project.title }}</h1>
    <p>{{ project.description }}</p> -->
    <!-- eslint-disable-next-line vue/no-v-html -->
    <article class="text-white p-4" v-html="content"></article>
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

  async asyncData({ params }) {
    try {
      const fileContent = await import(
        `@/static/projects/${params.projectDetail}/${params.projectDetail}.md`
      )
      return {
        content: fileContent.default
      }
    } catch (err) {
      return {
        content: `<h2>TUTU! There is no Markdown file found for this project!</h2><p>${err}</p>`
      }
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
