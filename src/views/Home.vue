<template>
  <div class="home">
    <h1>Hallo!</h1>
    <p class="subtitle">Ich bin Xayah Baumann</p>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
};
</script>

<style lang="scss">
.home {
  margin: auto;
  color: white;
  text-align: center;

  h1 {
    font-size: 42px;
    font-family: "Arvo", serif;
    //text-transform: uppercase;
  }

  .subtitle {
    color: rgb(189, 189, 189);
    line-height: 60px;
  }
}
</style>