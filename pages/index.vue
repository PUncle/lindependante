<template>
  <main class="wrapper flex mb-4 flex-wrap justify-start mx-auto">
    <Header />
    <ProjectCard
      v-for="project in projects"
      :key="project.slug"
      :title="project.title"
      :subtitle="project.subtitle"
      :slug="project.slug"
      :description="project.description"
      :thumb="project.thumb"
      :category="project.category"
    />
    <Footer />
  </main>
</template>

<script>
import Header from '~/components/Header'
import Footer from '~/components/Footer'
import ProjectCard from '~/components/ProjectCard'

export default {
  components: {
    Header,
    ProjectCard,
    Footer
  },
  data() {
    return {
      // ...data
    }
  },
  computed: {
    projects() {
      return this.$store.state.projects.projects
    }
  }
  // methods: {
  //   pathify(title) {
  //     return title
  //       .normalize('NFD')
  //       .replace(/[\u0300-\u036f]/g, '')
  //       .replace(/[^a-z0-9]+/gi, '-')
  //       .replace(/^-+/, '')
  //       .replace(/-+$/, '')
  //       .toLowerCase()
  //   }
  // }
}
</script>

<style>
/* .min-height {
  min-height: 20rem;
} */
</style>
