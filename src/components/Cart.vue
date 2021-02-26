 <template>
  <div class="cart">
   
    <div
      v-if="orderPlaced"
    >
    </div>
    <ul class="list-group">
      <li class="list-group-item" v-for="item in cart" :key="item.id">
        <button
          @click="removeItemFromCart(item.id)"
          type="button"
          class="close"
          data-dismiss="modal"
          aria-label="Close"
        >
          <span aria-hidden="true">&times;</span>
        </button>
        <div class="media">
          <img width="100px" :src="item.imgUrl" class="mr-3" alt="item.title" />
          <div class="media-body">
            <p class="nd mt-0">{{ item.title }}</p>
            <b-button class="qty-button btn btn-sm " variant="outline-danger" @click="reduceQty(item.id)">-</b-button>
             {{ item.qty }}
            <b-button
              class="qty-button btn btn-sm " variant="outline-success"
              @click="addQty(item.id)"
            >+</b-button>
          </div>
        </div>
      </li>
    </ul>
    
    <button
      v-if="cart.length"
      @click="placeOrder"
      class="checkout-button btn btn-lg btn-block btn-success"
      :disabled="isProcessing"
    >
      <div v-if="isProcessing" class="spinner-border" role="status">
        <span class="sr-only">Loading...</span>
      </div>
      <span v-else>Total {{ totalPrice.toLocaleString() }} บาท</span>
    </button>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Cart",
  data() {
    return {
      isProcessing: false,
      orderPlaced: false
    };
  },
  computed: {
    ...mapGetters(["cart"]),
    totalPrice() {
      return this.cart.reduce((a, b) => a + b.qty * b.price, 0);
    }
  },
  methods: {
    ...mapActions(["removeItemFromCart", "addQty", "reduceQty", "emptyCart"]),
    placeOrder() {
      this.isProcessing = true;
      setTimeout(() => {
        this.isProcessing = false;
        this.orderPlaced = true;
        this.emptyCart();
      }, 1000);
    }
  }
};
</script>

<style scoped>
.media {
  width: 90%;
  text-align: left;
}

.qty-button {
  width: 30px;
}

.checkout-button {
  margin-top: 20px;
}

.media-body{
  padding-left: 2rem;
}

.nd{
  padding-left: 0.3rem;
}
</style>