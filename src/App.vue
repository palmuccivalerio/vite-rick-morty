<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CardsList from "./components/CardsList.vue";

export default {
  components: {
    AppHeader,
    CardsList,
  },
  data() {
    return {
      cardsArray: [],
    };
  },
  created() {
    axios
      .get("https://rickandmortyapi.com/api/character", {
        params: {
          num: 20,
          offset: 0,
        },
      })
      .then((resp) => {
        this.cardsArray = resp.data.results;
        console.log(this.cardsArray);
      });
  },
};
</script>

<template>
  <AppHeader />
  <CardsList :cardsArray="cardsArray" />
</template>

<style lang="scss"></style>