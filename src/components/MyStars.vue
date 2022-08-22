<template>
  <div>
    Voto: 
    <i v-for="n in 5" :key="n" class="fa-star" :class="n <= starsCalc ? 'fa-solid' : 'fa-regular'"></i>
  </div>
</template>


<script>
export default {
  name: "MyStars",
  props: {
    vote: Number,
  },
  computed: {
    starsCalc() {
      return Math.ceil(this.vote / 2);
    },
  },
};
</script> 

<style scoped>
.fa-star {
    color: gold;
}


</style>