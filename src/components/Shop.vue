<template>
  <div class="row">
     <div
      class="card"
      style="width: 25rem; margin-left: 8rem;  background-color: rgb(202, 191, 212);"
      v-for="item in products"
      :key="item.id"
    >
      <b-card no-body class="overflow-hidden" >
        <b-row no-gutters>
          <b-col md-0>
            <b-card-img
              :src="item.imgUrl"
              class="card-img-top"
              :alt="item.title"
              tag="article"
            ></b-card-img>
          </b-col>
          <b-col>
            <b-card-text>
              <b-card-title>{{ item.title }}</b-card-title>
              <b-card-text>$ {{ item.price.toLocaleString() }}</b-card-text>
              <b-button variant="outline-success" @click="addItemToCart(item)">
                Add to cart
              </b-button>
            </b-card-text>
          </b-col>
        </b-row>
      </b-card>
      <!-- <img :src="item.imgUrl" class="card-img-top" :alt="item.title" />
      <div class="card-body">
        <p class="card-title">{{ item.title }}</p>
        <p class="card-text">$ {{ item.price.toLocaleString() }}</p>
        <button class="btn btn-primary" @click="addItemToCart(item)">
          Add to cart
        </button>
      </div> -->
    </div>
   
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";

export default {
  name: "Shop",
  mounted() {
    this.getProducts();
  },
  computed: {
    ...mapGetters(["products"]),
  },
  methods: {
    ...mapActions(["addItemToCart", "getProducts"]),
  },
};
</script>

<style scoped>
.card {
  padding: 10px;
  border: none;
}
</style>
