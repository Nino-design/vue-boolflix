<template>
  <div id="app">
    <!--COLLEGAMENTO DATI IMMESSI NEEL BARRA DI RICERCA-->
    <AppHeader @userSearch="findMovie($event)" />
    <main>
      <AppMain :films="filmsArray" :series="seriesArray" />
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
      seriesArray: [],
    };
  },
  /*RICHIESTA ARRAY OGGETTI DA SERVER*/
  methods: {
    findMovie: function (elementKey) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=f529d351b2c225b3c812601da9044977&query=" +
            elementKey
        )
        .then((resp) => {
          this.filmsArray = resp.data.results;
        });
      axios
        .get(
          "https://api.themoviedb.org/3/search/tv?api_key=f529d351b2c225b3c812601da9044977&query=" +
            elementKey
        )
        .then((resp) => {
          this.seriesArray = resp.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
