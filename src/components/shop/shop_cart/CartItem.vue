<template>
  <div class="cart-item">
    <h3 class="cart-title">{{ cart_item_data.title }}</h3>
    <div class="cart-quantity">
      Количество:
      <i @click="minusQuantity" class="fa-solid fa-circle-minus cart-btn"></i>
      <span class="cart-quantity-item">{{ cart_item_data.quantity }}</span>
      <i @click="plusQuantity" class="fa-solid fa-circle-plus cart-btn"></i>
    </div>
    <div class="cart-img">
      <img
        :src="require(`@/assets/img/rick/${cart_item_data.id}.jpg`)"
        alt="img"
      />
    </div>
    <my-button class="cart-btn" @click="deleteFromCart">Удалить</my-button>
  </div>
</template>

<script>
export default {
  props: {
    cart_item_data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {};
  },
  methods: {
    deleteFromCart() {
      this.$emit('deleteFromCart');
    },
    plusQuantity() {
      this.$emit("plusQuantity");
    },
    minusQuantity() {
      this.$emit("minusQuantity");
    },
  },
  mounted() {
    
  },
};
</script>

<style scoped>
.cart-item {
  display: grid;
  grid-template-columns: 2fr 2fr 2fr 1fr;
  grid-template-areas:
    "i . . ."
    "i t q b"
    "i . . .";
  border: 0.5px solid var(--black);
  padding: 1rem;
  border-radius: 4px;
  gap: 0.5rem;
}
.cart-title {
  grid-area: t;
  text-align: center;
  align-self: center;
}
.cart-img {
  grid-area: i;
  text-align: center;
  align-self: center;
}
.cart-btn {
  grid-area: b;
  text-align: center;
  align-self: center;
}

.cart-quantity {
  grid-area: q;
  font-weight: 700;  
  text-align: center;
  align-self: center;
  align-items: center;
  align-content: center;
  user-select: none;
}

.cart-quantity-item {
  margin-bottom: 5px;
  color: var(--black);
}

.cart-quantity i {
  font-size: 24px;
  margin: 0px 5px 0px 5px;
  cursor: pointer;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* .cart-btn {
  font-size: 24px;
  margin: 5px 10px 0px 10px;
  cursor: pointer;
} */
</style>
