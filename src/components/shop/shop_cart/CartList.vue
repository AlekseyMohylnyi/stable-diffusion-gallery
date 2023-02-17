<template>
  <div class="cart">
    <div class="shop-info">
      <div class="shop-total"><b>Общая сумма покупки:</b> {{ totalPrice }} $</div>
    </div>
    <transition-group name="cart-list">
      <cart-item
        v-for="(item, index) in cart_data"
        :key="item.id"
        :cart_item_data="item"
        @deleteFromCart="deleteFromCart(index)"
        @plusQuantity="plusQuantity(index)"
        @minusQuantity="minusQuantity(index)"
      />
    </transition-group>
  </div>
</template>

<script>
import CartItem from "@/components/shop/shop_cart/CartItem.vue";
import { mapActions } from "vuex";

export default {
  components: {
    CartItem,
  },
  props: {
    cart_data: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  computed: {
    totalPrice() {
      let result = [];

      if (this.cart_data.length) {
        for (let item of this.cart_data) {
          result.push(item.price * item.quantity);
        }
        result = result.reduce(function (sum, el) {
          return sum + el;
        });
        return result;
      } else {
        return 0;
      }
    },
  },
  methods: {
    ...mapActions({
      removeFromCart: "card/removeFromCart",
      incrementQuantity: "card/incrementQuantity",
      decrementQuantity: "card/decrementQuantity",
    }),
    deleteFromCart(index) {
      this.removeFromCart(index);
    },
    plusQuantity(index) {
      this.incrementQuantity(index);
    },
    minusQuantity(index) {
      this.decrementQuantity(index);
    },
  },
};
</script>

<style scoped>
.cart {
  display: grid;
  row-gap: 1rem;
}

.cart-title {
  text-align: center;
}
.cart-list-title {
  margin: 1rem 0;
}
.cart-list-item {
  display: inline-block;
  margin-right: 10px;
}
.cart-list-enter-active,
.cart-list-leave-active {
  transition: all 0.4s ease;
}
.cart-list-enter-from,
.cart-list-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
.cart-list-move {
  transition: transform 0.8s ease;
}
</style>
