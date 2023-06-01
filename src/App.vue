<template>
  <div id="app">
    <ShopHeader @search="handleSearch" />
    <ShopBody />
    <ShopFooter />
  </div>
</template>

<script>
import ShopHeader from './components/ShopHeader.vue'
import ShopFooter from './components/ShopFooter.vue'
import ShopBody from './components/ShopBody.vue'

export default {
  name: 'App',
  components: {
    ShopHeader,
    ShopBody,
    ShopFooter,
  },
  data() {
    return {
      searchText: '',
    };
  },
  methods: {
    handleSearch(text) {
      this.searchText = text;
    },
  },
}
</script>

<style lang="scss">
@import './styles/colors';
@import './styles/default';

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Merriweather', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  display: flex;
  flex-direction: column;
  min-height: 100vh;
  color: $text-brown;

  h1 {
    font-size: 24px;
    font-weight: 700;
  }

  h2 {
    font-size: 18px;
    font-weight: 400;
  }

  h3 {
    font-size: 16px;
    font-weight: 700;
  }

  h4 {
    font-size: 14px;
    font-weight: 700;
  }

  h5 {
    font-size: 14px;
    font-weight: 400;
  }

  h6 {
    font-size: 14px;
    font-weight: 300;
  }

  .container {
    margin: 0 auto;
    width: 1216px;
  }
}

@media screen and (max-width: 1240px) {
  #app {
    .container {
      width: 980px;
    }
  }
}

@media screen and (max-width: 980px) {
  #app {
    .container {
      width: 866px;
    }
  }
}

@media screen and (max-width: 866px) {
  #app {
    .container {    
      width: 580px;
    }
  }
}

@media screen and (max-width: 540px) {

  #app {

    h1 {
      font-size: 16px;
    }

    h2 {
      font-size: 12px;
    }

    h3 {
      font-size: 12px;
    }

    h4 {
      font-size: 10px;
    }

    h5 {
      font-size: 10px;
    }

    h6 {
      font-size: 10px;
    }

    .container {
      width: auto;

      &.header-container {
        padding: 24px 0;

        .header-search {
          height: 36px;

          &__input {
            width: 180px;
            height: 36px;
          }
        }
      }

    }
  }
}

@media screen and (max-width: 460px) {

  .header-container {

    .header-search {
      height: 36px;

      &__input {
        width: 180px;
        height: 36px;
      }
    }
  }
}
</style>
