
<template>
  <div class="d-flex justify-content-center">
    <div class="cards h-100 border-0">
      <figure class="m-0">
        <img
          class="copertina"
          v-if="info.poster_path === null"
          src="/Copertina-non-disponibile.jpg"
          alt="posterNotAvaible"
        />
        <img
          class="copertina"
          v-else
          :src="`http://image.tmdb.org/t/p/w342/${info.poster_path}`"
        />
      </figure>

      <div id="retroCard">
        <ul class="show">
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

export default {
  name: "MySearch",
  components: {
    MyStars,
  },
  props: {
    info: Object,
    type: String,
    languages: Array,
  },
};
</script>

<style scoped lang="scss">
@import "@/assets/sass/style.scss";


.cards {
  background-color: $bg-color-black;
  height: 500px;
  width: 342px;

  .copertina {
    width: 342px;
    height: 500px;
  }

  &:hover {
    width: 342px;
  }
}

.cards:hover .copertina {
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
}

.description {
  max-height: 350px;
  overflow-y: auto;
}
</style> 