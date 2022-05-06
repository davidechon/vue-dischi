<template>
  <header>
    <img src="https://grafica-facile.com/wp-content/uploads/2022/01/spotify-logo.png" alt="logo" class="logo">
  </header>
</template>

<script>
export default {
name: 'AppHeader',
}

</script>

<style lang="scss" scope>
@import '../assets/style/variable.scss';

header{
  background: $bg-color; 

  .logo {
    width: 50px;
    top: 10px;
    left: 10px;
  }

}



</style>