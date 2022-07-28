@@ -0,0 +1,21 @@
<template>
  <div class="hello">
    <ul>
      <li>
        <strong
          >Titolo: {{info.title }}
        </strong>
      </li>
      <li>
        <strong>Titolo originale: </strong>
        {{ info.original_title}}
      </li>
      <li>
        <strong>Lingua: {{ info.original_language }}</strong>
      </li>
      <li>
        <strong>Voto:{{ info.vote_average }}</strong>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "MySearch",
  props: {
    info: Object,
    type: String,
  },
};
</script>

<style scoped lang="scss">
</style> 