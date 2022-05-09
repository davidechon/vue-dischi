<template>
    <div class="d-flex justify-content-end align-content-center">
      <select name="genre" id="genre" v-model="select" @change="changeSearch">
        <option value>All</option>
        <option :value="genre" v-for="(item, index) in albumGenre" :key="index">{{genre}}</option>
        <!-- <option :value="album" v-for="(album, index) in albumAlbum" :key="index">{{album}}</option> -->
        
        <!-- <option value="3">Author</option> -->
       </select>
    </div>


</template>

<script>
export default {
  name: "AppSelect",
  data(){
    return {
      inputText: '',
    };
  },
  props:['albumGenre'],

  methods:{
    changeSearch(){
      this.$emit("performSearch, this.inputText");
    }
  },
};
</script>

<style lang="scss" scope>
@import "@/style/general.scss";
@import "@/style/variable.scss";

header {
  height: 70px;
  margin-bottom: 30px;
  position: relative;
  background: $bg-color;

  .logo {
    position: absolute;
    top: 10px;
    left: 20px;
    width: 40px;
    height: 40px;
    line-height: 70px;
  }
}
</style>