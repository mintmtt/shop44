<template>
  <header>
    <nav class="navbar navbar-light" style="background-color: #9370DB;">
      <span class="navbar-brand mb-0 h1" style="text-align: center;">Flowers Shop</span>
    </nav>
  </header>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "Header",
  computed: {
    ...mapGetters(['cart']),
    totalQty() {
      return this.cart.reduce((a, b) => a + b.qty, 0);
    },
  },
};
</script>

<style scoped>
header {
  margin-bottom: 4rem;
}
</style>