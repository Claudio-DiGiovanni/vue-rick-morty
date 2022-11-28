<template>
  <div>
    <pageHeader />
    <pageMain />
    <pageFooter />
  </div>
</template>

<script>
import pageHeader from '@/components/pageHeader.vue';
import pageMain from '@/components/pageMain.vue';
import pageFooter from '@/components/pageFooter.vue';

export default {
  components: {
    pageHeader,
    pageMain,
    pageFooter,
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap"
</style>
