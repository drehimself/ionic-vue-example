<template>
  <div class="hello">
    <ion-header>
      <ion-toolbar>
        <ion-title>Reddit clone /r/aww</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-list>
      <ion-item v-for="post in posts" :key="post.data.id" @click="handleClick(post.data.preview.images[0].source.url)">
        <img :src="post.data.thumbnail" alt="thumb" class="thumbnail">
        <ion-label>{{ post.data.title }}</ion-label>
      </ion-item>
    </ion-list>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted() {
    axios.get('https://www.reddit.com/r/aww.json?raw_json=1')
      .then(response => {
        this.posts = response.data.data.children
      })
  },
  data() {
    return {
      posts: [],
      myInput: ''
    }
  },
  methods: {
    handleClick(imageSrc) {
      this.$router.push({ name: 'about', params: { imageSrc }})
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .thumbnail {
    width: 60px;
    height: 60px;
    border-radius: 30px;
    margin-right: 16px;
    margin-top: 10px;
    margin-bottom: 10px;
  }
</style>
