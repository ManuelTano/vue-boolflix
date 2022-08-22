<template>
  <main>
    <div class="padd">
      <h2 class="mb-5 text-center">FILM</h2>
    </div>
    <div class="d-flex flex-wrap justify-content-center">
      <MySearch
        v-for="movie in movies"
        :key="movie.id"
        :info="movie"
        :type="'movie'"
        :languages="languages"
      />
    </div>

    <div>
      <h2 class="my-5 text-center">SERIE TV</h2>
    </div>
    <div class="d-flex flex-wrap justify-content-center">
      <MySearch
        v-for="serie in series"
        :key="serie.id"
        :info="serie"
        :type="'serie'"
        :languages="languages"
      />
    </div>
  </main>
</template>

<script>
import MySearch from "./MySearch.vue";

export default {
  name: "MyMain",
  components: {
    MySearch,
  },
  props: {
    movies: Array,
    series: Array,
    languages: Array,
  },
};
</script>

<style scoped lang="scss">
.padd {
  padding-top: 120px;
}

h2 {
  margin-left: 35px;
  color: white;
  font-weight: bold;
}

</style> 