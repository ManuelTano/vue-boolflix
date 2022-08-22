
<template>
  <div class="row">
    <div class="cards h-100 border-0 mb-5 mx-4">
      <figure class="m-0">
        <img
          class="cover"
          v-if="info.poster_path === null"
          src="/Copertina-non-disponibile.jpg"
          alt="Covernotavailable"
        />
        <img
          class="cover"
          v-else
          :src="`http://image.tmdb.org/t/p/w342/${info.poster_path}`"
        />
      </figure>

      <div id="retroCard ">
        <ul class="show ">
          <li class="mt-4">
            <strong
              >Titolo: {{ type === "movie" ? info.title : info.name }}
            </strong>
          </li>
          <li>
            <strong>Titolo originale: </strong>
            {{ type === "movie" ? info.original_title : info.original_name }}
          </li>
          <li>
            <strong>Lingua: </strong>

            <img
              v-if="languages.includes(info.original_language)"
              :src="require(`../assets/flags/${info.original_language}.png`)"
              alt="flags"
              class="flags"
            />
            <span class="text-uppercase" v-else>
              {{ info.original_language }}</span
            >
          </li>
          <li>
            <strong><MyStars :vote="info.vote_average" /></strong>
          </li>
              <li>
            <span class="fw-bold">Cast:</span>
            <span v-for="actor in cast" :key="actor.id"> {{ actor.name }}</span>
          </li>
          <li>
            <div class="description">
              <strong>Trama:</strong> {{ info.overview }}
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import MyStars from "./MyStars.vue";
import axios from "axios";

export default {
  name: "MySearch",
  components: {
    MyStars,
  },
  data() {
    return {
      cast: [],
    };
  },
  props: {
    info: Object,
    type: String,
    languages: Array,
  },
  
  methods: {
    getCast() {
      const type = this.info.title === "movie" ? "movie" : "tv";
      axios
        .get(
          `https://api.themoviedb.org/3/${type}/${this.info.id}/credits?api_key=1f5bacfe2502b312d524db09dc4b7175`
        )
        .then((results) => {
          const cast = results.data.cast;
          console.log(cast);
          cast.splice(5);
          this.cast = cast;
        });
    },
  },
  mounted() {
    this.getCast();
}
};
</script>

<style scoped lang="scss">
@import "@/assets/sass/style.scss";


.cards {
  background-color: $bg-color-black;
  max-height: 500px;
  width: 342px;

  .cover {
    width: 342px;
    height: 500px;
  }

  &:hover {
    width: 342px;
    height: 500px;
  }
}

.cards:hover .cover {
  display: none;
}

.show {
  color: $primary-color;
  display: none;
}
.cards:hover .show {
  display: block;
}

.flags {
  width: 20px;
}
ul {
  list-style-type: none;
  padding: 0;
  margin-left: 15px;
  margin-right: 15px;
}

.description {
  max-height: 320px;
  overflow-y: auto;
}



</style> 