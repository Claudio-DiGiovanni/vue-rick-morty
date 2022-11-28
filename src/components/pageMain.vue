<template>
  <div>
    <div class="container">
      <div class="row row-cols-4 g-5" v-if="arrCharacters">
      <cardCharacter
      v-for="character in arrCharacters"
      :key="character.id"
      :imgUrl="character.image"
      :name="character.name"
      :origin="character.origin.name"
      :species="character.species"
      />
    </div>
    <div v-else>Loading...</div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import cardCharacter from '@/components/cardCharacters.vue';

export default {
  name: 'pageMain',
  components: {
    cardCharacter,
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
};
</script>

<style lang="scss" scoped>

</style>
