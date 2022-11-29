<template>
  <div>
    <label for="s">
      <input type="text" name="s" id="s" v-model="searchString" @keyup.enter="search">
    </label>
    <button @click="search">Cerca</button>
  </div>
</template>

<script>
export default {
  name: 'searchBar',
  data() {
    return {
      searchString: '',
    };
  },
  methods: {
    search() {
      this.$emit('search', this.searchString);
    },
  },
};
</script>

<style>

</style>
