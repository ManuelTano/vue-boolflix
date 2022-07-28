<template>
  <div>
    <MySearch
      v-for="movie in movies"
      :key="movie.id"
      :info="movie"
      :type="'movie'"
      :languages="languages"
    />
  </div>
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
</style> 