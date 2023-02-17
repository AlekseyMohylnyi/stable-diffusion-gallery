<template>
  <div class="card">
    <h3 class="card-title">{{ card.title }}</h3>
    <h5 class="card-price">Цена: <br />{{ card.price }} $</h5>
    <div class="card-img">
      <img
        @click="showDialog"
        :src="require(`@/assets/img/rick/${card.id}.jpg`)"
        alt="img"
      />
    </div>
    <my-button class="info-btn" @click="showDialog">Посмотреть</my-button>
    <my-button class="card-btn" @click="addToCart">Добавить</my-button>
  </div>
</template>

<script>
export default {
  props: {
    card: {
      type: Object,
      requried: true,
    },
  },
  methods: {
    addToCart() {
      this.$emit("addToCart", this.card);
    },
    showDialog() {
      this.$emit("showDialog", this.card);
    },
  },
};
</script>

<style scoped>
.card {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-areas:
    "i i i"
    "i i i"
    "t t t"
    "p p ."
    "inf . b";
  border: 0.5px solid var(--black);
  padding: 1rem;
  border-radius: 4px;
  gap: 5px;
}
.card-title {
  grid-area: t;
  text-align: left;
  align-self: top;
}

.card-price {
  grid-area: p;
  text-align: left;
  align-self: flex-end;
}

.card-img {
  grid-area: i;
  text-align: center;
  align-self: top;
}

.card-img img {
  width: 100%;
  height: 240px;
  object-fit: cover;
}
.card-btn {
  grid-area: b;
  align-self: end;
  padding: 2px 4px;
}
.info-btn {
  grid-area: inf;
  align-self: end;
  padding: 2px 4px;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>