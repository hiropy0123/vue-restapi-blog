<template>
  <ul>
    <li v-for="post in posts" class="post-list-item" v-bind:key="post.id">
      <div class="article-title"><a v-bind:href="post.link">{{post.title.rendered}}</a></div>
      <div v-html="post.excerpt.rendered"></div>
      <!-- <img v-bind:src="image" alt=""> -->
    </li>
  </ul>
</template>

<style lang="scss" scoped>
ul {
  list-style: none;
}
.post-list-item {
  margin-bottom: 3rem;
  border-bottom: 1px dashed #ccc;
}
.article-title {
  font-size: 24px;
  font-weight: 700;
}
a {
  color: #c717bf;
  text-decoration: none;
  &:focus {
    color: darken(#c717bf, 15%);
  }
}
</style>

<script>
import axios from 'axios'
const POST_END_POINT = 'http://blog.alexcodesign.work'

export default {
  name: 'Blog',
  data: function() {
    return {
      posts: [],
      image: []
    }
  },
  mounted() {
    axios.get(POST_END_POINT + '/wp-json/wp/v2/posts')
      .then( response => {
        this.posts = response.data
      } ).catch( error => {
        console.log( error )
      } )
  }

}
</script>

