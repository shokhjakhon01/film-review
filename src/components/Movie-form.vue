<template>
  <div class="movie-form">
    <h3>Yangi kino qo'shish</h3>
    <form action="" class="add-form d-flex" @submit.prevent>
      <input
        type="text"
        class="form-control new-movie-label"
        placeholder="Qanday kino"
        :value="name"
        @input="name = $event.target.value"
      />
      <input
        type="text"
        class="form-control new-movie-label"
        placeholder="Nechi marotaba korilgan"
        :value="viewers"
        @input="viewers = $event.target.value"
      />
      <PrimaryButton class="btn-outline-dark" type="submit" @click="addMovie">
        Add film
      </PrimaryButton>
    </form>
  </div>
</template>

<script>
import PrimaryButton from "../ui-components/PrimaryButton.vue";
export default {
  data() {
    return {
      name: "",
      viewers: "",
    };
  },
  components: {
    PrimaryButton,
  },
  methods: {
    addMovie() {
      if (!this.name || !this.viewers) return;
      const newMovie = {
        id: Date.now(),
        title: this.name,
        year: this.viewers,
        like: false,
        favourite: false,
      };
      this.$emit("createMovie", newMovie);
      this.name = "";
      this.viewers = "";
    },
  },
};
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
