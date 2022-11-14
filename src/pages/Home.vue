<template>
<div class="page">
  <div class="informations">
    <div class="title">
      <h1>Per</h1>
      <span>if</span>
    </div>
    <p>Identidade visual acessiva e inclusiva para seu negócio</p>
    <p>Venda mais criando artes incríveis</p>
  </div>
  <div class="form">
    <div class="file-input">
    <input class="file" type="file" id="file" @change="setImage" />
    <label for="file">Insira a imagem do produto</label>
  </div>

  <label class="title-label" for="title">Título do Produto</label>
  <input type="text" id="title" class="title-input" v-model="title" placeholder="Insira o título" />

  <label class="price-label" for="price">Insira o Preço</label>
  <input class="price-input" type="text" id="price" v-model="price" placeholder="Insira o preço"/>
  <label class="post-type-label">Selecione o modelo de post</label>
  <div class="post-type">
    <button class="first-option" @click="postType=0" :disabled="postType===0"></button>
    <button class="second-option" @click="postType=1" :disabled="postType===1"></button>
    <button class="third-option" @click="postType=2" :disabled="postType===2"></button>
    <button class="blocked-option" @click="postType=2" disabled><span class="material-symbols-outlined">
lock
</span></button>
    <button class="blocked-option" @click="postType=2" disabled><span class="material-symbols-outlined">
lock
</span></button>
  </div>

  <Post id="post" v-if="image" class="post" :title="title" :price="price" :image="image" :post-type="postType"/>
  <button v-if="image" class="download-button" @click="convertPostToImage">Baixar Imagem</button>
  <div v-else class="empty-post">
    <span class="material-symbols-outlined">attach_file</span>
  </div>
  </div>
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
    price: 'R$',
    image: '',
    postType: 0,
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
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
}
.informations {
  display: flex;
  padding: 20px 20px 0 20px;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 500px;
  height: 670px;
  background: white;
  border-radius: 10px 0 0 10px;
}
.title {
  justify-content: center;
  display: flex;
  flex-direction: row;
  font-family: 'Pacifico', 'Arial';
  align-items: center;
  margin-bottom: 10px;
}
.title h1 {
  color: black;
  margin: 0;
  font-weight: 400;
  font-size: 70px;
}
.title span {
  font-size: 70px;
  font-weight: bold;
  color: #98c0d6;
}
p {
  color: black;
  font-weight: 600;
  margin: 10px;
  font-size: 20px;
}
.form {
  align-items: center;
  background: white;
  border-radius: 0 10px 10px 0;
  height: 670px;
  width: 320px;
  padding: 20px 20px 0 20px;
  display: flex;
  flex-direction: column;
}
.file-input {
  cursor: pointer;
  border: none;
  background: #98c0d6;
  padding: 6px;
  border-radius: 5px;
  margin-bottom: 10px;
  font-size: 14px;
}
.file-input:hover {
  background: #cde5f2;
}
.file-input label {
  cursor: pointer;
}
.file {
  display: none;
}

label {
  color: black;
  text-align: left;
  font-weight: 600;
  font-size: 14px;
}
input {
  margin-top: 3px;
  padding: 12px;
  border-radius: 5px;
  border: 1px solid #808080;
}
.price-label {
  margin-top: 10px;
  text-align: left;
  font-weight: bold;
  font-size: 14px;
}
.post-type-label {
  margin-top: 10px;
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
}
button:disabled {
  cursor: default;
  opacity: 0.6;
  border: 1px solid black;
}
.first-option {
  background-image: url('../static/assets/post_yellow.png');
  background-size: cover;
  width: 10px;
  padding: 20px;
}
.second-option {
  background-image: url('../static/assets/post_pink.png');
  background-size: cover;
  width: 10px;
  padding: 20px;
}
.third-option {
  background: green;
  padding: 20px;
}

.blocked-option {
  background: #98c0d6;
  padding: 7px;
}

.post {
  border: 1px solid black;
  margin: 0 auto;
}

.empty-post {
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid black;
  width: 300px;
  height: 300px;
}
.empty-post span {
  font-size: 80px;
  font-weight: bold;
  color: black;
}

.download-button {
  border: none;
  margin-top: 10px;
  background: #98c0d6;
  color: black;
  font-weight: 600;
  font-size: 14px;
}

.download-button:hover {
  border: none;
  background: #cde5f2;
}

@media only screen and (max-width: 950px) {
  .page {
    flex-direction: column;
  }
   input {
    width: 300px;
  }
  .informations {
    border-radius: 10px 10px 0 0;
    height: 250px;
  }
  .form {
    border-radius: 0 0 10px 10px;
    width: 500px;
  }
}

@media only screen and (max-width: 600px) {
  .informations {
    width: 300px;
    height: 200px;
  }
  input {
    width: 280px;
  }
  p {
    margin: 5px;
    font-size: 16px;
  }
  .form {
    width: 300px;
  }
}
</style>
