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
        class="col-6 col-md-4 col-lg-3 my-3 text-center"
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
        this.albumList = [res.data];
      }).catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scope>
@import "../assets/style/variable.scss";
</style>