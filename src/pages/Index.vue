<template>
  <Layout :show-logo="false">
    <!-- Author intro
    <Author :show-title="true" />
    -->
    <!-- List posts -->
    <div class="posts">
      <PostCard v-for="edge in $page.posts.edges" :key="edge.node.id" :post="edge.node"/>
    </div>

  </Layout>
</template>

<page-query>
query {
  posts: allPost(sortBy: "date", order: ASC, filter: { }) {
    edges {
      node {
        id
        date
        content
        fileInfo {
          name
        }
        path
      }
    }
  }
}
</page-query>

<script>
import Author from '~/components/Author.vue'
import PostCard from '~/components/PostCard.vue'

export default {
  components: {
    Author,
    PostCard
  },
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>
<style scoped>
.posts div:not(:first-child){
  page-break-before: always;
}
</style>
