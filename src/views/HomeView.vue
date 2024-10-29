<template>
  <div class="home">
    <MainSlide />
    <DomesticArticle :m="selectedCategory" />
  </div>
</template>

<script>
import MainSlide from '@/components/MainSlide.vue';
import DomesticArticle from '@/components/DomesticArticle.vue';

export default {
  name: 'HomeView',
  props: {
    selectedCategory: {
      type: String,
      default: 'articles',
    },
  },
  components: {
    MainSlide,
    DomesticArticle,
  },
};
</script>

<style lang="scss">
.home {
  width: 100%;
  height: auto;
}
</style>
