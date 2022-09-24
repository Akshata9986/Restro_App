<template>
  <h1>Little Indian Restro</h1>
  <ul>
    <dish-details
      v-for="dish in dishes"
      :key="dish.id"
      :id="dish.id"
      :name="dish.name"
      :img="dish.img"
      :description="dish.description"
      :price="dish.price"
      :isFavourite="dish.isFavourite"
      @toggleFavouriteStatus="toggleFavouriteStatus"
    />
  </ul>
</template>

<script>
import DishDetails from "./components/DishDetails.vue";
export default {
  name: "App",
  components: { DishDetails },
  data() {
    return {
      dishes: [
        {
          id: "avi",
          name: "Butter Chicken",
          img: "https://media.istockphoto.com/photos/murgh-makhani-butter-chicken-tikka-masala-picture-id1262857001?b=1&k=20&m=1262857001&s=170667a&w=0&h=LDytMWvxGKBs63GhCuAxxYnG1MDibHLmNH8mij4gkPA=",
          description: "It's finger licking good",
          price: 350,
          isFavourite: true,
        },
        {
          id: "vaibhav",
          name: "Chole Bhature",
          img: "https://media.gettyimages.com/photos/closeup-chole-bhature-served-at-table-picture-id552154821?s=612x612",
          description: "The crispy puffed bhatura and gravy",
          price: 150,
          isFavourite: false,
        },
        {
          id: "akshata",
          name: "Fish Fry",
          img: "https://media.istockphoto.com/photos/tasty-grilled-fish-picture-id980462262?b=1&k=20&m=980462262&s=170667a&w=0&h=Xj7Oxu5kA57vZMXaWD917tuhpJ7JAII8G1sPKtyOT-U=",
          description: "includes french fries,coleslaw",
          price: 300,
          isFavourite: false,
        },
      ],
    };
  },
  methods: {
    //to get dishDetails from child component
    toggleFavouriteStatus(dishID) {
      // console.log("dish ID in parent", dishID);
      let identifiedDish = this.dishes.find((dish) => dish.id === dishID);
      identifiedDish.isFavourite = !identifiedDish.isFavourite;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app h1 {
  background-color: blueviolet;
}
</style>