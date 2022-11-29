<!-- eslint-disable max-len -->
<template>
  <div>
    <searchBar @search="search" />
    <div class="container">
      <div class="row row-cols-4 g-5" v-if="arrCharacters">
        <cardCharacter v-for="character in arrCharacters" :key="character.id" :imgUrl="character.image"
          :name="character.name" :origin="character.origin.name" :species="character.species" />
      </div>
      <div v-else>Loading...</div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import cardCharacter from '@/components/cardCharacters.vue';
import searchBar from '@/components/searchBar.vue';

export default {
  name: 'pageMain',
  components: {
    cardCharacter,
    searchBar,
  },
  data() {
    return {
      arrCharacters: null,
      urlApi: 'https://rickandmortyapi.com/api/character',
    };
  },
  created() {
    // scaricare i dati
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        this.arrCharacters = axiosResponse.data.results;
      });
  },
  methods: {
    search(searchString) {
      axios.get(this.urlApi, {
        params: {
          name: searchString,
        },
      })
        .then((axiosResponse) => {
          console.log(axiosResponse);
          this.arrCharacters = axiosResponse.data.results;
        })
        .catch((error) => {
          console.log(error);
          if (error.response.status === 404
            && error.response.data.error === 'There is nothing here'
          ) {
            this.arrCharacters = [];
          }
        });
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
