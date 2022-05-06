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
  <div class="container">
    <!-- 
    img 
    titolo
    autore
    anno
    -->
    <div v-for="(album, index) in albumList" :key="index">
      <img :src="album.img" :alt="album.title" />
    </div>
    <div :class="title">{{ albumList.title }}</div>
    <div :class="author">{{ album.author }}</div>
    <div :class="year">{{ album.year }}</div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AppGrid",
  data() {
    return {
      albumList: [],
      apiPath: "https://flynn.boolean.careers/exercises/api/array/music/",
    };
  },
  mouted() {
    axios.get(this.apiPath + `album`).then((res) => {
      console.log(res);
      this.albumList = [...res.data];
    });
  },
};
</script>

<style lang="scss" scope>
@import "../assets/style/variable.scss";
</style>