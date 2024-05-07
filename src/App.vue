<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CardsList from "./components/CardsList.vue";
import AppSearchBar from "./components/AppSearchBar.vue";

import { CalculationOperation } from "sass";

export default {
  components: {
    AppHeader,
    CardsList,
    AppSearchBar,
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
  methods: {
    typeStatus(){
      const  paramsObj= {status:""};
      if (this.store.status !== "all"){
        paramsObj.status=this.store.status
      }
     axios
      .get("https://rickandmortyapi.com/api/character", {
       params: paramsObj
      })
      .then((resp) => {
        this.cardsArray = resp.data.results;
        console.log(this.cardsArray);
      });
    }
    
  },
};
</script>

<template>
  <AppHeader />
  <AppSearchBar @filter="typeStatus"/>
  <CardsList :cardsArray="cardsArray" />
</template>

<style lang="scss"></style>