<template>
<div class="card-wrapper m-3 text-center">
    <h3 class="fw-bold mt-2 mb-2">{{ movie.title }}</h3>
    <h5 class="m-0">{{ movie.original_title }}</h5>
    <p>{{ movie.original_language }}</p>
    <p>{{ movie.vote_average }}</p>
  </div>
  
</template>

<script>
export default {
name: 'AppFilmsCards',
props: {
    movie: Object,
}
}
</script>

<style lang="scss" scoped>

.card-wrapper {
  width: calc(100% / 5);
  border: 1px solid black;
  color: white;
  }

</style>