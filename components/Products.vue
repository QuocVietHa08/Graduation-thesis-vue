<template>
  <div :class="[detail ? 'detail' : '']" class="rounded-2xl shadow-xl shadow-slate-300/60">
    <div class="img-wrapper rounded-t-2xl">
      <nuxt-link
        :to="{
          name: 'product_detail-id',
          params: {
            id: product.id,
            title: product.title,
            price: product.price,
            rating: product.ratings,
            reviews: product.reviews,
            isAddedBtn: product.isAddedBtn
          }
        }"
      >
        <img class="rounded-t-2xl" src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
      </nuxt-link>
    </div>
    <div class="text-wrapper p-4">
      <div class="flex items-center justify-between mb-3">
        <div class="media-content">
          <nuxt-link
              :to="{
                name: 'product_detail-id',
                params: {
                  id: product.id,
                  title: product.title,
                  price: product.price,
                  rating: product.ratings,
                  reviews: product.reviews,
                  isAddedBtn: product.isAddedBtn
                }
              }"
            >
            <span :class="[detail ? 'text-3xl' : 'text-lg']">{{ product.title }}</span>
          </nuxt-link>
        </div>
        <button class="button text-lg" :title="removeFromFavouriteLabel" v-show="product.isFavourite" @click="removeFromFavourite(product.id)">
          <span class="icon">
            <i class="fas fa-heart"></i>
          </span>
        </button>
        <button class="button text-lg" :title="addToFavouriteLabel" v-show="!product.isFavourite" @click="saveToFavorite(product.id)">
          <span class="icon">
            <i class="far fa-heart"></i>
          </span>
        </button>
      </div>
      <div class="content is-clearfix">
        <p :class="[detail ? 'text-2xl' : 'text-base']">{{ product.description }}</p>
        <div class="flex justify-between">
          <div class="flex items-center">
            <i v-if="product.ratings === 1" class="fa fa-star"></i>
            <i v-if="product.ratings === 2" class="fa fa-star"></i>
            <i v-if="product.ratings === 2" class="fa fa-star"></i>
            <i v-if="product.ratings === 3" class="fa fa-star"></i>
            <i v-if="product.ratings === 3" class="fa fa-star"></i>
            <i v-if="product.ratings === 3" class="fa fa-star"></i>
            <i v-if="product.ratings === 4" class="fa fa-star"></i>
            <i v-if="product.ratings === 4" class="fa fa-star"></i>
            <i v-if="product.ratings === 4" class="fa fa-star"></i>
            <i v-if="product.ratings === 4" class="fa fa-star"></i>
            <i v-if="product.ratings === 5" class="fa fa-star"></i>
            <i v-if="product.ratings === 5" class="fa fa-star"></i>
            <i v-if="product.ratings === 5" class="fa fa-star"></i>
            <i v-if="product.ratings === 5" class="fa fa-star"></i>
            <i v-if="product.ratings === 5" class="fa fa-star"></i>
            <p class="ml-2 text-lg">{{ product.reviews > 0 ? `${product.reviews} Reviews` : 'No reviews' }}</p>
          </div>
          <p class="text-3xl font-medium">
            <strong>&euro; {{ product.price }}</strong>
          </p>
        </div>
        <div class="flex justify-between mt-5 items-center">
          <!-- <select class="p-2 border-2 rounded-2xl" @change="onSelectQuantity(product.id)" v-model="selected">
            <option
              v-bind:key="quantity"
              v-for="quantity in quantityArray"
              :value="quantity"
            >
              {{ quantity }}
            </option>
          </select> -->
          <button class="rounded-xl bg-button p-3 text-white" v-if="!product.isAddedToCart" @click="handleBuyProduct(product.id)">{{ buyNowLabel }}</button>
          <button class="rounded-xl p-3" v-if="product.isAddedToCart" @click="removeFromCart(product.id, false)">{{ removeFromCartLabel }}</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Swal from 'sweetalert2'

export default {
  name: 'products',
  props: ['product', 'detail'],
  components: [
    'Swal',
  ],
  data () {
    return {
      buyNowLabel: 'Buy now',
      viewDetailsLabel: 'Details',
      removeFromCartLabel: 'Remove from cart',
      addToFavouriteLabel: 'Add to favourite',
      removeFromFavouriteLabel: 'Remove from favourite',
      selected: 1,
      quantityArray: []
    }
  },

  mounted () {
    for (let i = 1; i <= 20; i++) {
      this.quantityArray.push(i);
    }

    if (this.$props.product.quantity > 1) {
      this.selected = this.$props.product.quantity;
    }
  },

  computed: {
    isUserLogged () {
      return this.$store.getters.isUserLoggedIn;
    }
  },

  methods: {
    addToCart (id) {
      let data = {
        id: id,
        status: true
      }
      this.$store.commit('addToCart', id);
      this.$store.commit('setAddedBtn', data);
    },
    removeFromCart (id) {
      let data = {
        id: id,
        status: false
      }
      this.$store.commit('removeFromCart', id);
      this.$store.commit('setAddedBtn', data);
    },
    saveToFavorite (id) {
      let isUserLogged = this.$store.state.userInfo.isLoggedIn;

      if (isUserLogged) {
        this.$store.commit('addToFavourite', id);
      } else {
        this.$store.commit('showLoginModal', true);
      }
    },
    removeFromFavourite (id) {
      this.$store.commit('removeFromFavourite', id);
    },
    onSelectQuantity (id) {
      let data = {
        id: id,
        quantity: this.selected
      }
      this.$store.commit('quantity', data);
    },
    async handleBuyProduct(id) {
      console.log("hello:", id)

      
      
    await ethereum
    .request({
      method: 'eth_sendTransaction',
      params: [
        {
          from: '0x95903BE0DF352cf5CB97c646B89E231099632990',
          to: '0xbE01F13f55dFC9cDAe7475FEa3198de7B1499EEB',
          value: '0x01a2241af62c0000',
        },
      ],
    })
    .then((txHash) => {
      console.log(txHash)
       Swal.fire({
        toast: true,
        icon: 'success',
        position: 'top-end',
        text: `Hash: ${txHash.slice(0,30)}`,
        timer: 2000,
        showConfirmButton: false,
      })
    })
    .catch((error) => {
       Swal.fire({
        toast: true,
        icon: 'error',
        position: 'top-end',
        text: `Error: ${error}}`,
        timer: 2000,
        showConfirmButton: false,
      }) 
    });
    }
  }
}
</script>

<style lang="scss" scoped>
  .bg-button {
    background-color: #9cbe11;
  }

  .detail {
    padding: 20px;
    @apply flex;
    @apply flex-col;
    @apply lg:flex-row;
    @apply shadow-2xl;

    .img-wrapper {
      flex: 1;

      img {
        @apply lg:rounded-none;
        @apply lg:rounded-tl-2xl;
        @apply lg:rounded-bl-2xl;
      }
    }

    .text-wrapper {
      flex: 2;
    }
  }
</style>
