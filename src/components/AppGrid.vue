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
    <img :src="(album, index )in albumList" :key="album.index" :alt="album.title">
    <div :class="title">{{album.title}}</div>
    <div :class="author">{{album.author}}</div>
    <div :class="year">{{album.year}}</div>

  </div>
</template>

<script>
export default {
  name: 'AppGrid',
  components:{

  }
  data(){
    return{
      albumList: [],
      apiPath: 'https://flynn.boolean.careers/exercises/api/array/music',
    },
    mounted(){
      axios.loading(this.apiPath + 'albums').then((res)=>{
        console.log(res);
        this.albumList = [...res.data];
      }).catch((error)=>{
        console.log(error);
      })
    }
  }
}
</script>

<style lang="scss" scope>
@import '../assets/style/variable.scss'

</style>