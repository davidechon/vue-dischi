<template>
    <div class="d-flex justify-content-end align-content-center">
      <select name="genre" id="genre" v-model="inputText" @change="mySelect">
      <option value="genre">All</option>
      <option value="genre" v-for="(genre, index) in albumGenre" :key="index">{{genre}}</option>
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
    reset(){
      this.inputText='';
      this.$emit('mySearch', this.inputText)
    },
    mySelect(){
      this.$emit('mySelect', this.inputText)
      this.inputText='';
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