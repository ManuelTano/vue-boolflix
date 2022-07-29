<template>
  <div>
    Voto: 
    <i v-for="star in starsCalc" :key="star" class="fas fa-star ms-1"></i>
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
.fas {
    color: gold;
}


</style>