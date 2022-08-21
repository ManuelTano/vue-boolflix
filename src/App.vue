<template>
  <div id="app">
    <MyHeader @searching="Search" />
    <MyMain :movies="movies" :series="series" :languages="languages" />
  </div>
</template>

<script>
import axios from "axios";
import MyHeader from "./components/MyHeader.vue";
import MyMain from "./components/MyMain.vue";
import "./assets/sass/style.scss";

export default {
  name: "App",
  components: {
    MyHeader,
    MyMain,
  },
  data() {
    return {
      movies: [],
      series: [],
      languages: ["it", "en"],
      api_key: "1f5bacfe2502b312d524db09dc4b7175",
    };
  },
  methods: {
    searchMovies(query) {
      const params = {
        query: query,
        api_key: this.api_key,
      };
      return axios
        .get(`https://api.themoviedb.org/3/search/movie`, { params })
        .then((response) => {
          this.movies = response.data.results;
        });
    },

    searchSeries(query) {
      const params = {
        query: query,
        api_key: this.api_key,
      };
      return axios
        .get(`https://api.themoviedb.org/3/search/tv`, { params })
        .then((response) => {
          this.series = response.data.results;
        });
    },

    Search(query) {
      this.searchMovies(query);
      this.searchSeries(query);
    },
  },
};
</script>

<style lang="scss">

body{
  margin: 0 auto;
  box-sizing: border-box;
}
</style>
