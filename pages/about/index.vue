<template>
  <section id="about-page" v-editable="blok">
    <h1>{{ title }}</h1>
    <p>{{ content }}</p>
  </section>

</template>

<script>
  export default {
    asyncData(context) {
      return context.app.$storyapi.get('cdn/stories/about', {
        version: context.isDev ? 'draft' : 'published'
      })
        .then(response => {
          return {
            blok: response.data.story.content,
            title: response.data.story.content.title,
            content: response.data.story.content.content
          }
        })
    },
    mounted () {
      this.$storyblok.init()
      this.$storyblok.on('change', () => {
        location.reload(true)
      })
    }
  }
</script>

<style scoped>

</style>
