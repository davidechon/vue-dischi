<template>
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
  <div class="container">
    <!-- 
    img 
    titolo
    autore
    anno
    -->
    <div v-for="(album, index) in albumList" :key="index">
      <img :src="albumList.img" :alt="albumList.title">
    </div>
    <div :class="title">{{album.title}}</div>
    <div :class="author">{{album.author}}</div>
    <div :class="year">{{album.year}}</div>

  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'AppGrid',
  data(){
    return{
      albumList: [],
      apiPath: 'https://flynn.boolean.careers/exercises/api/array/music/',
    };
  },
    mounted(){
      axios.get(this.apiPath + 'albums').then((res)=>{
        console.log(res);
        this.albumList = [...res.data];
      }).catch((error)=>{
        console.log(error);
      });
    }
  }

</script>

<style lang="scss" scope>
@import '../assets/style/variable.scss';

</style>