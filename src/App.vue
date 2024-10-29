<template>
  <nav>
    <router-link to="/">
      <button class="main-logo"></button>
    </router-link>
    <div class="dropdown">
      <button class="main-dropdown" @click="toggleDropdown">{{ dropdownText }} <img src="../public/img/icon/icon_dropdown_down.svg"></button>
      <div v-if="dropdownVisible" class="dropdown-menu">
        <button @click="selectDomesticNews">국내 뉴스</button>
        <button @click="selectGlobalNews">해외 뉴스</button>
      </div>
    </div>
    <router-link to="/search">
      <button class="main-search"></button>
    </router-link>
  </nav>
  <router-view :selectedCategory="selectedCategory"/>
  <FooterView/>
</template>

<script>
import FooterView from '@/components/FooterView.vue';

export default {
  name: 'App',
  data() {
    return {
      dropdownVisible: false,
      selectedCategory: 'articles',
      dropdownText: '국내',
    };
  },
  components: {
    FooterView
  },
  methods: {
    toggleDropdown() {
      this.dropdownVisible = !this.dropdownVisible;
    },
    selectDomesticNews() {
      this.selectedCategory = 'articles';
      this.dropdownText = '국내';
      this.dropdownVisible = false;
    },
    selectGlobalNews() {
      this.selectedCategory = 'global-articles';
      this.dropdownText = '해외';
      this.dropdownVisible = false;
    },
  },
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html, body {
  width: 100%;
  height: 100%;
}

#app {
  max-width: 480px;
  width: auto;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 0 16px;
  margin: 0 auto;
}
nav {
  width: 100%;
  padding: 24px 0 16px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  a{
    display: flex;
    .main-logo {
      width: 80px;
      height: 20px;
      background: url('../public/img/news_logo.svg') no-repeat center;
      border: none;
    }
  }
  .main-search {
    width: 20px;
    height: 20px;
    margin-left: 60px;
    background: url('../public/img/icon/icon_search.svg') no-repeat center;
    border: none;
  }
  .dropdown {
    width: 60px;
    display: flex;
    justify-content: center;
    position: relative;
    .main-dropdown {
      font-size: 20px;
      font-weight: 600;
      color: #111;
      text-decoration: none;
      background-color: transparent;
      border: none;
      display: flex;
      align-items: center;
      gap: 4px;
    }
    .dropdown-menu {
      width: 80px;
      position: absolute;
      top: 30px;
      left: -15px;
      background-color: #fff;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      z-index: 10;
      button {
        width: 100%;
        display: block;
        border: none;
        background: transparent;
        padding: 10px;
        text-align: center;
      }
    }
  }
}
</style>
