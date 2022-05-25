<template>
  <div class="card-wrapper m-3 text-center">
    <h3 class="fw-bold mt-2 mb-2">{{ movie.title ? movie.title : movie.name }}</h3>
    <h5 class="m-0">{{ movie.original_title ? movie.original_title : movie.original_name }}</h5>
    <img v-if="haveImage" class="flag" :src="require(`../assets/img/${movie.original_language}.png`)" alt="">
    <p v-else>{{ movie.original_language }}</p>
    <p>Voto: {{ movie.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "AppFilmsCards",
  props: {
    movie: Object,
  },
  data() {
    return {
      flags: ['de', 'en', 'es', 'fr', 'it'],
    }
  },
  methods: {
    haveImage: function () { 
      return this.flags.includes(this.movie.original_language);
    }
  }
};
</script>

<style lang="scss" scoped>
.card-wrapper {
  width: calc(100% / 5);
  border: 1px solid black;
  color: white;
}

.flag{ 
  width: 20%;
}
</style>