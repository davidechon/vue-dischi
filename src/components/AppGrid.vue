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
    <div class="row d-flex flex-wrap g-5 justify-content-center">
      <div
        v-for="(item, index) in albumList"
        :key="index"
        class="card col col-sm-2 justify-content-center align-items-center"
      >
        <img :src="item.poster" :alt="item.title" />
        <div class="title-card">{{ item.title }}</div>
        <div class="text-card">{{ item.author }}</div>
        <div class="text-card">{{ item.genre }}</div>
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
  background: $bg-color;

  .card {
    background: $bg-card-color;
    height: 350px;

      img {
        width: 100%;
        height: 160px;
      }
      .title-card {
        color: $title-color;
      }
      .text-card {
        color: $text-color;
      }

  }
  
}

</style>