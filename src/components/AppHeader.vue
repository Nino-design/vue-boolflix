<template>
  <!--HEADER-->
  <div
    class="
      header
      container-fluid
      d-flex
      justify-content-between
      align-items-center
    "
  >
    <h1 class="title">BOOLFLIX</h1>
    <div class="search">
      <!--INPUT E BUTTON-->
      <input type="text" placeholder="search" v-model="searchMovie" />
      <button @click="$emit('userSearch', searchMovie)">Invia</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppHeader",
  data() {
    return {
      searchMovie: "",
    };
  },
};
</script>

<style lang="scss" scoped>
/*STILIZZAZIONE HEADER*/
.header {
  background-color: black;

  .title {
    color: red;
  }
}
</style>