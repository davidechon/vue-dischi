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
    <app-select  @mySearch="setSearchText" :albumGenre="genre"/>
    <app-loader v-if="loading"/>
    <div class="row row-cols-5 d-flex flex-wrap justify-content-center">
      <div
        v-for="(item, index) in filteredList"
        :key="index"
        class="card justify-content-center align-items-center"
      >
        <img :src="item.poster" :alt="item.title" />
        <h3 class="title-card">{{ item.title }}</h3>
        <div class="text-card">{{ item.author }}</div>
        <div class="text-card">{{ item.genre }}</div>
        <div class="text-card">{{ item.year }}</div>
      </div>
    </div>
  </section>
</template>

<script>
import AppLoader from "./AppLoader.vue";
import AppSelect from "./AppSelect.vue";
import axios from "axios";

export default {
  name: "AppGrid",
  components: {
    AppLoader,
    AppSelect,
  },
  data() {
    return {
      albumList: [],
      searchText:'',
      apiPath: "https://flynn.boolean.careers/exercises/api/array/",
      loading: false,
      genre: [],
    };
  },
  methods:{
    setSearchText(text){
      this.searchText = text;
    }
  },
  computed:{
    // searchText(){
    //   // state.search
    // },
    filteredList(){
      if(this.searchText===''){
        return this.albumList;
      }
      return this.albumList.filter((item)=>{
        return item.genre === this.searchText;
      });
    },
  },
  mounted() {
    this.loading = true;
    setTimeout(()=>{
      axios.get(this.apiPath + "music").then((res) => {
        console.log(res);
        this.albumList = res.data.response;
        this.albumList.forEach((item)=>{
          if(!this.genre.includes(item.genre)){
            this.genre.push(item.genre);
          }
        }),
        this.loading = false;
      }).catch((error) => {
        console.log(error);
        this.loading = false;
      });
    }, 3000);
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