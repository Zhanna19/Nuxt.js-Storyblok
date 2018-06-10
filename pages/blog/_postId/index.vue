<template>
  <div id="post" v-editable="blok">
    <div class="post-thumbnail" :style="{backgroundImage: 'url(' + image + ')'}"></div>
    <section class="post-content">
      <h1>{{ title }}</h1>
      <p>{{ content }}</p>
    </section>
  </div>
</template>

<script>
  export default {
    asyncData (context) {
      return context.app.$storyapi.get('cdn/stories/blog/' + context.params.postId, {
        version: context.isDev ? 'draft' : 'published'
      })
        .then(response => {
          console.log(response)
          return {
            blok: response.data.story.content,
            image: response.data.story.content.thumbnail,
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
  .post-thumbnail {
    width: 100%;
    height: 300px;
    background-size: cover;
    background-position: center;
  }

  .post-content {
    width: 80%;
    max-width: 300px;
    margin: auto;
  }

  .post-content p {
    white-space: pre-line;
  }
</style>
