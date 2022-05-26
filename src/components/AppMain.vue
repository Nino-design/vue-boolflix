<template>
  <section>
    <div
      class="
        container
        d-flex
        justify-content-start
        align-items-center
        flex-wrap
        mt-5
        mb-5
      "
    >
      <AppFilmsCards
        v-for="element in films"
        :key="element.id"
        :movie="element"
      />
      <AppFilmsCards
        v-for="element in series"
        :key="element.id"
        :movie="element"
      />
    </div>
  </section>
</template>

<script>
import AppFilmsCards from "./AppFilmsCards.vue";
export default {
  name: "AppMain",
  components: {
    AppFilmsCards,
  },
  props: {
    films: Array,
    series: Array,
  },
};
</script>

<style lang="scss" scoped>
.container{
    transform-style: preserve-3d;
}


section {
  height: 100%;
  overflow: hidden;
  background-color: gray;
}
</style>