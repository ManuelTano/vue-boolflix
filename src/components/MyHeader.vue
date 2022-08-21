<template>
  <header>
    <div class="row h-100 mx-3">
      <div class="col-6 d-flex align-items-center">
        <figure class="m-0">
          <img src="/logo.png" alt="Logo Boolflix" />
        </figure>
      </div>

      <div class="col-6 d-flex align-items-center justify-content-end">
        <div class="d-flex">
          <input
            v-model="keyword"
            @keyup.enter="searchKeyword"
            type="text"
            class="form-control rounded mx-2"
            placeholder="Cerca film o serietv.."
            aria-label="Search"
          />

          <button
            @click="searchKeyword"
            type="button"
            class="btn btn-outline-danger rounded"
          >
            Cerca
          </button>
        </div>
      </div>
    </div>
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
@import "@/assets/sass/style.scss";

header {
  height: 100px;
  background-color: $bg-color-black;
  position: fixed;
  min-width: 100%;
}
img {
  max-height: 50px;
  width: 200px;
}

</style> 