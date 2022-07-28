<template>
  <header>
    <input
      v-model="keyword"
      @keyup.enter="searchKeyword"
      type="text"
      class="form-control rounded"
      placeholder="Cerca il tuo film"
      aria-label="Search"
    />
    <button @click="searchKeyword" class="btn">Cerca</button>
  </header>
</template>

<script>
export default {
  name: "MyHeader",
  data() {
    return {
      keyword: "",
    };
  },
  methods: {
    searchKeyword() {
      this.$emit("searching", this.keyword);
    },
  },
};
</script>

<style scoped lang="scss">
</style> 