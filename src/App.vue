<template>
  <div id="app">
    <AppHeader @userSearch="findMovie($event)"/>
    <main>
      <AppMain :films="filmsArray"/>
    </main>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
      filmsArray: [],
    }
  },
  methods: { 
    findMovie: function (movieKey) {
      axios
      .get("https://api.themoviedb.org/3/search/movie?api_key=f529d351b2c225b3c812601da9044977&query=" + movieKey)
      .then((resp) => {
        console.log(resp);
        this.filmsArray = resp.data.results;
      });
    }
  }
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
