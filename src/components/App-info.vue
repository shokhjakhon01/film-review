<template>
  <Box class="app-info">
    <p class="fs-3 text-uppercase">Barcha kinolar soni: {{ allMovies }}</p>
    <p class="fs-4 text-uppercase">
      Korilgan kinolar soni: {{ favouriteMovies }}
    </p>
  </Box>
</template>

<script>
import Box from "../ui-components/Box.vue";
export default {
  props: {
    allMovies: {
      type: Number,
      required: true,
    },
    favouriteMovies: {
      type: Number,
      required: true,
    },
  },
  components: { Box },
};
</script>

<style scoped></style>
