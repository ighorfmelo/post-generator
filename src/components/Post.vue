<template>
  <div class="image-background" :style="{background: postColor}">
    <h1 v-text="title" />
    <h2 v-text="price" />
    <div class="image-container" >
      <img :src="image" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Post',
  props: {
    title: String,
    price: String,
    image: String,
    postColor: String,
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
  h1 {
    font-size: 26px;
    padding: 5%;
    text-align: left;
    position: absolute;
    top: 0;
    left: 0;
    margin: 0;
    color: white;
    z-index: 3;
  }

  h2 {
    padding: 5%;
    position: absolute;
    color: white;
    margin: 0;
    z-index: 3;
    bottom: 0;
    right: 0;
  }
  .image-container {
    border-radius: 50%;
    position: absolute;
    overflow: hidden;
    width: calc(100% - 30%);
    height: calc(100% - 30%);
  }

  img {
    position: relative;
    width: 100%;
    height: 100%;
  }
</style>