<template>
  <div class="app-info">
    <p class="fs-3 text-uppercase">Barcha kinolar soni: {{ allMovies }}</p>
    <p class="fs-4 text-uppercase">Korilgan kinolar soni: {{ favouriteMovies }}</p>
  </div>
</template>

<script>

export default {
  props: {
    allMovies: {
      type: Number,
      required: true
    },
    favouriteMovies: {
      type: Number,
      required: true
    }
  }
}
</script>

<style scoped>
.app-info {
  margin-top: 2rem;
  background-color: #fcfaf5;
  padding: 1.5rem;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>