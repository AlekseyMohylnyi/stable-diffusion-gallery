<template>
  <div class="card-list">
    <catalog-item
      v-for="card in cards"
      :key="card.id"
      :card="card"
      @addToCart="addToCart"
      @showDialog="openDialog(card)"
    />
    <my-dialog v-model:show="dialogVisible">
      <dialog-item
      :dialog_card="dialogCard"
      @closeDialog="closeDialog"
      @addToCart="addToCart"
      />
    </my-dialog>
  </div>
</template>

<script>
import CatalogItem from "./CatalogItem.vue";
import DialogItem from "./DialogItem.vue";
import { mapGetters, mapActions } from "vuex";
export default {
  components: {
    CatalogItem,
    DialogItem,
  },
  data() {
    return {
      dialogVisible: false,
      dialogCard: [],
    };
  },
  methods: {
    ...mapActions({
      fetchCards: "card/fetchCards",
      moveToCart: "card/moveToCart",
    }),
    addToCart(data) {
      this.moveToCart(data);
    },
    openDialog(card) {
      this.dialogVisible = true;
      this.dialogCard = card;
    },
    closeDialog() {
      this.dialogVisible = false;
    },
  },
  mounted() {
    this.fetchCards();
  },
  computed: {
    ...mapGetters({
      cards: "card/getCards",
    }),
  },
};
</script>

<style scoped>
.card-list {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-gap: 1rem;
}

@media screen and (max-width: 768px) {
  .card-list {
    grid-template-columns: 1fr 1fr;
    grid-gap: 0.2rem;
  }
}

@media screen and (max-width: 420px) {
  .card-list {
    grid-template-columns: 1fr;
    grid-gap: none;
  }
}
</style>