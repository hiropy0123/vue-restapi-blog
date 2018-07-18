<template>
  <div class="home">
    <h1>Topics</h1>
    <Blog />
  </div>
</template>

<script>
import Blog from '@/components/Blog'

export default {
  name: 'home',
  components: {
    Blog
  }
}
</script>
