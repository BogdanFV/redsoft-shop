<template>
  <div class="body-container container">
    <h1 class="body__header">{{ title }}</h1>
    <div class="cards-container">
      <div v-for="product in filteredProducts" :key="product.id" :class="{
        'card': true,
        'card--disabled': !product.active
      }">
        <img :src="require(`../assets/cards-photos/${product.image}`)" :alt="product.name" class="card__image">
        <div class="card-text">
          <h2 class="card-text__title">{{ product.name }}</h2>
          <div v-if="product.active" class="card-text__activity">
            <div v-if="product.oldPrice" class="card-text__price">
              <h6 class="card-text__old-price">{{ product.oldPrice }}</h6>
              <h3 class="card-text__new-price">{{ product.price }}</h3>
            </div>
            <h3 v-else class="card-text__price">{{ product.price }}</h3>
            <BuyButton class="card-text__button" :productId="product.id" />
          </div>
          <div v-else class="card-text-disabled">
            <h3 class="card-text__sold">Продано на аукционе</h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BuyButton from './BuyButton.vue';
import { products } from '../products.js'

export default {
  components: {
    BuyButton,
  },
  data() {
    return {
      title: 'Картины эпохи Возрождения',
    };
  },
  computed: {
    filteredProducts() {
      if (!this.$parent.searchText) {
        return products;
      } else {
        const searchText = this.$parent.searchText.toLowerCase();
        return products.filter((product) =>
          product.name.toLowerCase().includes(searchText)
        );
      }
    },
  },
};

</script>

<style lang="scss">
.body__header {
  margin-top: 45px;
  margin-bottom: 39px;
}

h2 {
  text-align: left;
}

h6 {
  text-decoration-line: line-through;
  color: #A0A0A0;
}

.body-container {
  flex: 1;
  min-height: 768px;

  .cards-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;

    .card {
      width: 280px;
      border: 1px solid #E1E1E1;
      text-align: center;
      margin-bottom: 32px;
      display: flex;
      flex-direction: column;

      &--disabled {
        opacity: 0.5;
      }

      &__image {
        width: 100%;
        height: auto;
      }

      &-text {
        padding: 20px 24px 24px;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;

        &__title {
          margin-bottom: 22px;
        }

        &__activity {
          display: flex;
          flex-direction: row;
          align-items: center;
          width: 100%;
        }

        &__price {
          text-align: left;
        }

        &__button {
          margin-left: auto;
          width: 118px;
        }

        &__sold {
          margin: 12px 0;
        }
      }
    }
  }
}

@media screen and (max-width: 600px) {
  .body-container {

    display: flex;
    flex-direction: column;
    align-items: center;

    .cards-container {
      flex-direction: column;

      .card {
        width: 400px;
      }
    }
  }
}
</style>
