<template>
  <div class="image-background">
    <img class="background" :src="`../../static/assets/${background}`" alt="">
    <h1 v-text="title" :class="`post-h1-${postType}`" />
    <h2 v-text="price" :class="`post-h2-${postType}`" />
    <img class="image" :src="image" alt="">
  </div>
</template>

<script>
export default {
  name: 'Post',
  props: {
    title: String,
    price: String,
    image: String,
    postType: Number,
  },
  data: () => ({
    images: ['post_yellow.png', 'post_pink.png']
  }),
  computed: {
    background() {
      return this.images[this.postType]
    }
  }
}
</script>

<style scoped>
  .image-background {
    position: relative;
    display: flex;
    width: 300px;
    height: 300px;
    justify-content: center;
    background: blue;
    align-items: center;
  }
  .background {
    z-index: 3;
    width: 300px;
    height: 300px;
  }
  h1 {
    font-family: 'Pacifico', 'Arial';
    font-weight: bold;
    font-size: 26px;
    padding: 5%;
    position: absolute;
    transform: rotate(-5deg);
    margin: 0;
    color: black;
    z-index: 3;
  }

  h2 {
    font-family: 'Pacifico', 'Arial';
    transform: rotate(-5deg);
    position: absolute;
    color: black;
    margin: 0;
    z-index: 3;
  }

  .post-h1-0 {
    bottom: 0;
  }


  .post-h2-0 {
    top: 60px;
    right: 10px;
  }

  .post-h1-1 {
    top: 5px;
    color: white;
  }


  .post-h2-1 {
    bottom: 55px;
    right: 20px;
  }

  .image {
    z-index: 2;
    position: absolute;
    overflow: hidden;
    width: 300px;
    height: 300px;
  }
</style>