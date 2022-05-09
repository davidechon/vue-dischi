<template>
  <header>
    <img
      src="https://grafica-facile.com/wp-content/uploads/2022/01/spotify-logo.png"
      alt="logo"
      class="logo"
    />

  </header>
</template>

<script>

export default {
  name: "AppHeader", 
  components:{
 
  }      
}
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