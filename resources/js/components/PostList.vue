<template>
  <div>
    <h1>Post List will be here</h1>
    <div v-for="post in posts" :key="post.id">
      <h1>{{post.title}}</h1>
      <p>{{post.excerpt}}</p>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      posts: [],
      meta: null,
      links: null
    };
  },
  created() {
    const token = this.$cookie.get('api_token');
    const url = `/api/v1/post?api_token=${token}`;
    axios.get(url).then(response => {
      this.posts = response.data.data;
      this.meta = response.data.meta;
      this.links = response.data.links;
    });
  }
};
</script> 