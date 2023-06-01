<template>
  <button @click="handleBuy" :class="{ 'in-cart': isInCart, 'loading': isLoading, 'brown': isInCart }">
    <h4 v-if="!isLoading && !isInCart">Купить</h4>
    <span v-else-if="isLoading">
      <span class="loading-icon"></span>
    </span>
    <span v-else class="stashed-icon"><img src="../assets/icons/ok-icon.svg" alt="location"
        class="stashed-icon__img" />
      <h4>В корзине</h4>
    </span>
  </button>
</template>

<script>
export default {
  props: {
    productId: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      isInCart: false,
      isLoading: false
    };
  },
  mounted() {
    this.isInCart = this.getCartItemState(this.productId);
  },
  methods: {
    handleBuy() {
      if (this.isLoading) return;

      this.isLoading = true;
      if (this.isInCart) {
        this.resetCartItem();
      } else {
        fetch('https://jsonplaceholder.typicode.com/posts/1', {
          method: 'GET'
        })
          .then((response) => response.json())
          .then(() => {
            this.isInCart = true;
            this.isLoading = false;
            this.saveCartItemState(this.productId, this.isInCart);
          })
          .catch((error) => {
            console.error(error);
            this.isLoading = false;
          });
      }
    },
    resetCartItem() {
      this.isInCart = false;
      this.isLoading = false;
      this.saveCartItemState(this.productId, this.isInCart);
    },
    saveCartItemState(productId, isInCart) {
      localStorage.setItem(`cartItem-${productId}`, JSON.stringify(isInCart));
    },
    getCartItemState(productId) {
      const itemState = localStorage.getItem(`cartItem-${productId}`);
      return itemState ? JSON.parse(itemState) : false;
    }
  }
};
</script>