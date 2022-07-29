@@ -0,0 +1,21 @@
<template>
  <div class="hello">
    <ul>
      <li>
        <img
          id="copertina"
          :src="`http://image.tmdb.org/t/p/w342/${info.poster_path}`"
        />
      </li>
      <li>
        <strong
          >Titolo: {{ type === "movie" ? info.title : info.name }}
        </strong>
      </li>
      <li>
        <strong>Titolo originale: </strong>
        {{ type === "movie" ? info.original_title : info.original_name }}
      </li>
      <li>
        <strong>Lingua:</strong>
        <img
          v-if="languages.includes(info.original_language)"
          :src="`/flags/${info.original_language}.png `"
          alt="flags"
        />
        <span class="text-uppercase" v-else> {{ info.original_language }}</span>
      </li>
      <li>
        <strong><MyStars :vote="info.vote_average"/></strong>
      </li>
    </ul>
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
img {
  margin-left: 5px;
  width: 20px;
  height: 10px;
}

#copertina {
  width: 200px;
  height: 300px;
}

</style> 