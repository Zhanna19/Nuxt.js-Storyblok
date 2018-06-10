<template>
  <section id="posts" class="container">
    <PostPreview
      v-for="post in posts"
      :key="post.id"
      :title="post.title"
      :excerpt="post.previewText"
      :thumbnailImage="post.thumbnail"
      :id="post.id"></PostPreview>
  </section>
</template>

<script>

  import PostPreview from "@/components/Blog/PostPreview";
  export default {
    components: {
      PostPreview
    },
    asyncData (context) {
      return context.app.$storyapi.get('cdn/stories', {
        starts_with: 'blog',
        version: context.isDev ? 'draft' : 'published'
      })
        .then(response => {
          console.log(response)
          return {
            posts: response.data.stories.map(bp => {
              return {
                id: bp.slug,
                title: bp.content.title,
                previewText: bp.content.summary,
                thumbnail: bp.content.thumbnail
              }
            })
          }
        })
    }
    // data () {
    //   return {
    //     posts: [
    //       {
    //         title: 'A New Beginning',
    //         previewText: 'This will be awesome, don\'t miss it!',
    //         thumbnail: 'http://www.pravda-tv.ru/wp-content/uploads/2014/02/new-beginnings_t_nv.jpg',
    //         id: 'a-new-beginning'
    //       },
    //       {
    //         title: 'Second Beginning',
    //         previewText: 'This will be awesome, don\'t miss it!',
    //         thumbnail: 'http://www.pravda-tv.ru/wp-content/uploads/2014/02/new-beginnings_t_nv.jpg',
    //         id: 'second-beginning'
    //       }
    //     ]
    //   }
    // }
  }
</script>

<style scoped>
  #posts {
    padding-top: 2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  @media (min-width: 35rem) {
    #posts {
      flex-direction: row;
    }
  }
</style>
