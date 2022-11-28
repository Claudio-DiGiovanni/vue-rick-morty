<template>
  <div class="col">
    <div class="contents text-center">
      <img class="img-fluid rounded-circle"
      :src="imgUrl"
      :alt="name"
      >
      <h2 class="name">
        {{ name }}
      </h2>
      <div class="origin">
        {{ origin }}
      </div>
      <div class="species">
        {{ species }}
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'cardCharacters',
  props: {
    imgUrl: String,
    name: String,
    origin: String,
    species: String,
  },
};
</script>

<style lang="scss" scoped>

</style>
