<template>
  <header>
    <div>
      <div>
        <b-navbar
          toggleable="lg"
          type="dark"
          variant="danger"
          class="navbar-horizontal"
        >
          <b-navbar-brand href="#">FLOWERS SHOP</b-navbar-brand>
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        </b-navbar>
      </div>
    </div>
  </header>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "Header",
  computed: {
    ...mapGetters(["cart"]),
    totalQty() {
      return this.cart.reduce((a, b) => a + b.qty, 0);
    },
  },
};
</script>

<style scoped>
header {
  margin-bottom: 2rem;
}
.navbar-brand {
  text-align: center;
}
</style>
