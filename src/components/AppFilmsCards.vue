<template>
  <!--STRUTTURA CARDS-->
  <div class="card-wrapper m-3 text-center">
    <div class="card-content">
      <div class="card-front">
        <!--AGGIUNTA DINAMICA POSTERS-->
        <img
          class="poster"
          v-if="movie.poster_path"
          :src="`http://image.tmdb.org/t/p/w300/${movie.poster_path}`"
          alt=""
        />
        <!--AGGIUNTA IMMAGINE NO POSTER-->
        <img
          v-else
          class="no-image"
          src="../assets/img/no-image-available-icon-flat-vector-no-image-available-icon.jpg"
          alt=""
        />
      </div>
      <!--DISCRIMINARE SERIE DA FILMS-->
      <dir class="card-back">
        <h3 class="fw-bold fs-4">
          {{ movie.title ? movie.title : movie.name }}
        </h3>
        <h5 class="m-0">
          {{
            movie.original_title ? movie.original_title : movie.original_name
          }}
        </h5>
        <!--AGGIUNTA BANDIERA-->
        <img
          v-if="haveImage"
          class="flag"
          :src="require(`../assets/img/${movie.original_language}.png`)"
          alt=""
        />
        <!--AGGINTA LINGUA SE NON C'E' BANDIERA E VOTO-->
        <p v-else>{{ movie.original_language }}</p>
        <p>Voto: {{ movie.vote_average }}</p>
        <div class="stars">
          <span>
            <!--CREAZIONE STELLE PER VOTO-->
            <i
              v-for="element in 5"
              :key="element"
              class="fa fa-star"
              :class="element <= voteStars ? 'fas' : 'far'"
            ></i
          ></span>
        </div>
      </dir>
    </div>
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
      flags: ["de", "en", "es", "fr", "it"],
    };
  },
  /*FUNZIONI LINGUA E VOTO*/
  computed: {
    haveImage: function () {
      return this.flags.includes(this.movie.original_language);
    },
    voteStars: function () {
      return Math.ceil(this.movie.vote_average / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
/*STRUUTURA CARDS*/
.card-wrapper {
  width: calc(100% / 6 - 6px);
  height: 300px;
  color: white;
  position: relative;
  transform-style: preserve-3d;
  perspective: 1000px;
}

.card-content {
  width: 100%;
  height: 100%;
  position: relative;
  transform-style: preserve-3d;
  transition: transform 0.9s ease;
}

.card-front,
.card-back {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transform: translateZ(100px);
}

.card-back {
  padding: 1rem;
  transform: rotateY(180deg);
  background-color: black;
  backface-visibility: hidden;
}
/*EFFETTO HOVER*/
.card-content:hover {
  transform: rotateY(180deg);
}

.poster img {
  object-fit: cover;
}

.no-image {
  object-fit: fill;
  height: 270px;
}
.flag {
  width: 15%;
}
.stars span {
  color: yellow;
}
</style>