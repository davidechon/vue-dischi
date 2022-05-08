  <!-- {
  "success": true,
  "response": [
    {
      "poster": "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg",
      "title": "New Jersey",
      "author": "Bon Jovi",
      "genre": "Rock",
      "year": "1988"
    }
} -->
  
<template>
  <section class="container">
    <div class="row row-cols-5 d-flex flex-wrap justify-content-center">
      <div
        v-for="(item, index) in albumList"
        :key="index"
        class="card justify-content-center align-items-center"
      >
        <img :src="item.poster" :alt="item.title" />
        <h3 class="title-card">{{ item.title }}</h3>
        <div class="text-card">{{ item.author }}</div>
        <!-- <div class="text-card">{{ item.genre }}</div> -->
        <div class="text-card">{{ item.year }}</div>
      </div>
    </div>
    <!-- 
    img 
    titolo
    autore
    anno
    -->
  </section>
</template>

<script>
import axios from "axios";

export default {
  name: "AppGrid",
  data() {
    return {
      albumList: [],
      apiPath: "https://flynn.boolean.careers/exercises/api/array/",
    };
  },
  mounted() {
    axios.get(this.apiPath + "music").then((res) => {
        console.log(res);
        this.albumList = res.data.response;
      }).catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scope>
@import "@/assets/style/variable.scss";

.row{

  .card {
    background: $bg-color;
    width: calc((100% / 5) - 40px);
    margin: 10px 20px;
    display: block;
    text-align: center;

      img {
        width: 100%;
        height: 160px;
        margin: 10px auto;
      }
      .title-card {
        color: $title-color;
        font-size: 1.3em;
        text-transform: uppercase;
        text-align: center;
        margin: 10px 0 20px;
      }
      .text-card {
        color: $text-color;
        margin-bottom: 10px;
      }

  }
  
}

</style>