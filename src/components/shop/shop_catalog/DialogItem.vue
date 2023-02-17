<template>
  <div class="dialog">
    <div class="dialog-header">
      <h3 class="dialog-title">Карточка товара</h3>
      <i @click="closeDialog" class="fa-solid fa-circle-xmark"></i>
    </div>
    <h3 class="dialog-title-card">{{ dialog_card.title }}</h3>
    <h5 class="dialog-price">Цена: {{ dialog_card.price }} $</h5>
    <div class="dialog-img">
      <img
        :src="require(`@/assets/img/rick/${dialog_card.id}.jpg`)"
        alt="img"
      />
    </div>
    <my-button class="add-btn" @click="addToCart">В корзину</my-button>
    <my-button class="close-btn" @click="closeDialog">Закрыть</my-button>
  </div>
</template>

<script>
export default {
  props: {
    dialog_card: {
      type: Object,
      requried: true,
    },
  },
  methods: {
    addToCart() {
      this.$emit("addToCart", this.dialog_card);
    },
    closeDialog() {
      this.$emit("closeDialog");
    },
  },
};
</script>

<style scoped>
.dialog {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-areas:
    "h h h h"
    "i i i i"
    "i i i i"
    "t t t t"
    "p p . ."
    "a . . c";
  padding: 0.5rem;
  border-radius: 4px;
  row-gap: 10px;
}

.dialog-header {
  grid-area: h;
  display: grid;
  grid-auto-flow: column;
  grid-auto-columns: max-content;
  justify-content: space-between;
  align-items: center;
}

.dialog-header i {
  font-size: 32px;
  cursor: pointer;
  transition: color ease .2s;
}

.dialog-header i:hover {
  color: var(--bg-color);
  
}
.dialog-title-card {
  grid-area: t;
  text-align: left;
  align-self: top;
}

.dialog-price {
  grid-area: p;
  text-align: left;
  align-self: flex-end;
}

.dialog-img {
  grid-area: i;
  text-align: center;
  align-self: top;
  width: 100%;
  height: 300px;
}
.add-btn {
  grid-area: a;
  align-self: end;
  padding: 2px 4px;
}
.close-btn {
  grid-area: c;
  align-self: end;
  padding: 2px 4px;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>