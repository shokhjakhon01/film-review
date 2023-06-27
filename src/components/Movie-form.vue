<template >
  <div class="movie-form">
    <h3>Yangi kino qo'shish</h3>
    <form action="" class="add-form d-flex">
      <input type="text" class="form-control new-movie-label" placeholder="Qanday kino">
      <input type="text" class="form-control new-movie-label" placeholder="Nechi marotaba korilgan">

      <button class="btn btn-outline-dark" type="submit">Add film</button>
    </form>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.movie-form {
  margin-top: 2rem;
  background-color: #fcfaf5;
  padding: 1.5rem;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>