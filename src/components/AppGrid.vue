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
    <div class="row">
      <div
        v-for="(item, index) in albumList"
        :key="index"
        class="card col-6 col-md-4 col-lg-3 my-3 text-center"
      >
        <img :src="item.poster" :alt="item.title" />
        <div>titolo {{ item.title }}</div>
        <div>autore {{ item.author }}</div>
        <div>genre {{ item.genre }}</div>
        <div>anno{{ item.year }}</div>
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

$bg-color: #1e2d3b;
$bg-card-color: #2e3a46;
$title-color: #fffffb;
$text-color: #807873;

row{
  background: $bg-color;
  
}

card {
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

</style>