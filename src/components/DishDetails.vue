<template>
  <li>
    <h2>{{ name }} {{ isFavourite ? "🤤" : "" }}</h2>
    <button @click="toggleFavourite" style="color: blue">
      Toggle Favourite
    </button>
    <button @click="toggleDetails" style="color: navy blue">
      {{ displayDetails ? "Hide" : "Show" }}Details
    </button>
    <ul v-if="displayDetails">
      <li><strong>Description:</strong>{{ description }}</li>
      <li><strong>Price:</strong>{{ price }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  emits: ["toggleFavouriteStatus"],

  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    img: {
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    price: {
      type: Number,
      required: true,
    },
    isFavourite: {
      type: Boolean,
      required: false,
    },
  },
  data() {
    return {
      //   dishIsFavourite: this.isFavourite,
      displayDetails: false,
    };
  },
  methods: {
    toggleFavourite() {
      //   if (this.dishIsFavourite) {
      //     this.dishIsFavourite = false;
      //   } else {
      //     this.dishIsFavourite = true;
      //   }
      //   this.dishIsFavourite = !this.dishIsFavourite;
      this.$emit("toggleFavouriteStatus", this.id);
    },
    toggleDetails() {
      this.displayDetails = !this.displayDetails;
    },
  },
};
</script>

<style>
li {
  list-style-type: none;
}
</style>