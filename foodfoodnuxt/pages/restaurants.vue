<template>
  <main class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>

      <AppSelect @change="selectedRestaurant = $event" />
      <!-- <app-select @change="selectedRestaurant = $event" :selectoptions="restaurantOptions" /> -->
      <pre>{{ $data }}</pre>
    </div>

    <AppRestaurantInfo />
    <!-- <AppRestaurantInfo :datasource="filteredRestaurants" /> -->
  </main>
</template>

<script>
import AppRestaurantInfo from "@/components/AppRestaurantInfo.vue";
import AppSelect from '@/components/AppSelect.vue';

export default {
  components: {
    AppSelect,
    AppRestaurantInfo
  },
  data() {
    return {
      selectedRestaurant: "",
      // restaurantOptions: ["tacos", "pizza", "dim sum"],
    };
  },
};
</script>

<style lang="scss" scoped></style>
