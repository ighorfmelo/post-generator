<template>
<div class="page">
  <div class="file-input">
    <input class="file" type="file" id="file" @change="setImage" />
    <label for="file">Coloque uma imagem do seu produto</label>
  </div>

  <label class="title-label" for="title">Título do Produto</label>
  <input type="text" id="title" class="title-input" v-model="title" placeholder="Insira o título" />

  <label class="price-label" for="price">Insira o Preço</label>
  <input class="price-input" type="text" id="price" v-model="price" placeholder="Insira o preço"/>
  <div class="post-type">
    <button class="button-red" @click="postColor='red'"></button>
    <button class="button-blue" @click="postColor='blue'"></button>
    <button class="button-green" @click="postColor='green'"></button>
  </div>
  <Post id="post" v-if="image" class="post" :title="title" :price="price" :image="image" :post-color="postColor"/>

  <button class="download-button" @click="convertPostToImage">Baixar Imagem</button>
</div>
</template>

<script>
import Post from '../components/Post.vue'
import html2canvas from 'html2canvas';

export default {
  name: 'Page',
  components: {
    Post,
  },
  data: () => ({
    title: '',
    price: '',
    image: '',
    postColor: '',
  }),
  methods: {
    setImage(event) {
      this.image = URL.createObjectURL(event.target.files[0])
    },
    convertPostToImage() {
      if (!document.querySelector("#post")) return
      html2canvas(document.querySelector("#post")).then(canvas => {
        var link = document.createElement('a');
        link.download = 'post.png';
        link.href = canvas.toDataURL()
        link.click();
      });
    }
  }
}
</script>

<style scoped>
.page {
  width: 320px;
  display: flex;
  flex-direction: column;
}
.file-input {
  cursor: pointer;
  border: 1px solid black;
  padding: 6px;
  border-radius: 5px;
  margin-bottom: 10px;
  font-size: 14px;
}
.file-input label {
  cursor: pointer;
}
.file {
  display: none;
}

label {
  text-align: left;
  text-transform: uppercase;
  font-weight: bold;
  font-size: 14px;
}
input {
  margin-top: 6px;
  padding: 12px;
  border-radius: 5px;
  border: 1px solid gray;
}
.price-label {
  text-align: left;
  text-transform: uppercase;
  font-weight: bold;
  font-size: 14px;
}
.post-type {
  margin: 10px auto;
  display: flex;
  gap: 6px;
  flex-direction: row;
}
.post-type button {
  border-radius: 50%;
  border: none;
  padding: 20px;
}
.button-red {
  background: red;
}
.button-blue {
  background: blue;
}
.button-green {
  background: green;
}

.post {
  margin: 0 auto;
}

.download-button {
  border: none;
  margin-top: 10px;
  background: black;
  color: white;
}

.download-button:hover {
  border: none;
  background: rgba(0,0,0, 0.8);
}
</style>
