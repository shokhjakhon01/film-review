<template>
  <div class="btn-group">
    <PrimaryButton
      v-for="btn in filteredButtons"
      type="button"
      @click="filterHandler(btn.name)"
      :class="[filterName === btn.name ? 'btn-dark' : 'btn-outline-dark']"
    >
      {{ btn.title }}
    </PrimaryButton>
  </div>
</template>

<script>
import PrimaryButton from "../ui-components/PrimaryButton.vue";
export default {
  props: {
    updateFilterHandler: {
      type: Function,
      required: true,
    },
    filterName: {
      type: String,
      required: true,
    },
  },
  components: {
    PrimaryButton,
  },
  data() {
    return {
      filter: "all",
      filteredButtons: [
        {
          title: "Barcha kinolar",
          name: "all",
        },
        {
          title: "Mashhur kinolar",
          name: "popular",
        },
        {
          title: "Eng ko'p ko'rilgan kinolar",
          name: "mostViewers",
        },
      ],
    };
  },
  methods: {
    filterHandler(filter) {
      this.filter = filter;
      this.updateFilterHandler(this.filter);
    },
  },
};
</script>

<style scoped></style>
