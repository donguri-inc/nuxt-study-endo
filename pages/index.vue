<template lang="pug">
.container
  div
    p 自動ビルド
    div(v-for="post in posts")
      h1 {{ post.title.rendered }}
      .content(v-html="post.content.rendered")


</template>

<script>
export default {

  async asyncData({ params, error, payload, store, $axios }) {
      const res = await $axios.$get('http://nuxt-study-wp.don-guri.com/wp-json/wp/v2/posts/')
      return {
        posts: res
      }

    },
    mounted() {
      console.log(this.posts)
    },updated() {

    },



}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
