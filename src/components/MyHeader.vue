<template>
  <header>
    <input
      v-model="keyword"
      @keyup.enter="searchKeyword"
      type="text"
      class="form-control rounded mt-2 "
      placeholder="Cerca il tuo film o serietv"
      aria-label="Search"
    />
    <button @click="searchKeyword" class="btn btn-light mt-2 mb-5" >Cerca</button>
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