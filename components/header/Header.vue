<template>
  <nav
    class="flex justify-between sticky top-0 nav-style z-10 shadow-md px-3"
    role="navigation"
    aria-label="main navigation"
  >
    <div class="flex">
      <nuxt-link :to="{ name: 'index' }" class="navbar-item">
        <h1 class="text-3xl">K.U.N</h1>
      </nuxt-link>
      <div>
        <ul class="pages-container">
          <li v-for="{ title, url} in pages" :key="url">
              <nuxt-link :to="url"> {{ title }}</nuxt-link>
          </li>
        </ul>
      </div>
    </div>
    <div class="flex items-center">
      <!-- <div class="mx-2">
        <div class="cursor-pointer" @click="showCheckoutModal">
          <span
            :class="[
              numProductsAdded > 0 ? 'p-2 bg-blue text-white rounded-md' : ''
            ]"
            >{{ numProductsAdded }}</span
          >
          <span class="icon">
            <i class="fa fa-shopping-cart"></i>
          </span>
        </div>
      </div> -->

      <div class="mx-2 flex">
        <button class="flex" @click="handleConnectMetamask">
          <span class="icon">
            <i class="fa fa-user"></i>
          </span>
          <div class="ml-2" v-if="account.length === 0">Connect Metamask</div>
          <div class="ml-2"> {{ account.slice(0, 10) }} </div>
        </button>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "VmHeader",

  data() {
    return {
      pages: [
        {
          title: "Home",
          url: "/",
        },
        {
          title: "Contacts",
          url:"/contacts",
        },
        {
          title: "Store",
          url: "/store"
        }
      ],
      isCheckoutActive: false,
      showDropdown: false,
      logoutLabel: "Log out",
      loginLabel: "Log in",
      signupLabel: "Sign up",
      wishlistLabel: "Wishlist",
      account: ""
    };
  },

  computed: {
    numProductsAdded() {
      return this.$store.getters.productsAdded.length;
    },
    isUserLoggedIn() {
      return this.$store.getters.isUserLoggedIn;
    },
    getUserName() {
      let name = this.$store.getters.getUserName;

      if (name === "") {
        return "user";
      } else {
        return name;
      }
    }
  },

  mounted() {
    window.addEventListener("blur", this.closeDropdown, true);
  },
  destroyed() {
    window.removeEventListener("blur", this.closeDropdown);
  },

  methods: {
    closeDropdown() {
      setTimeout(() => {
        this.showDropdown = false;
      }, 100);
    },
    showCheckoutModal() {
      this.$store.commit("showCheckoutModal", true);
    },
    showLoginModal() {
      this.$store.commit("showLoginModal", true);
    },
    showSignupModal() {
      this.$store.commit("showSignupModal", true);
    },
    onShowDropdown() {
      this.showDropdown = !this.showDropdown;
    },
    logout() {
      this.$store.commit("isUserLoggedIn", false);
      this.$store.commit("isUserSignedUp", false);
      this.$store.commit("removeProductsFromFavourite");

      // redirect to homepage
      this.$router.push({ name: "index" });
    },
    async handleConnectMetamask() {
      if (typeof window.ethereum !== "undefined") {
        const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
        this.account = accounts[0];
        console.log(accounts)
      }
    },
    handleDisconnectMetamask() {
      console.log("handle disconnect metamask");
    }
  }
};
</script>

<style lang="scss" scoped>
.nav-style {
  background-color: #1d2c3e;
  color: white;
  padding: 15px 10px;
}
.pages-container {
  width: 20vw;
  height: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  li {
    padding: 5px;
  }
}
.title {
  background: url("../../static/vuemmerce-logo.png") no-repeat;
  background-position: 50% 50%;
  background-size: 165px;
}
.dropdown {
  @apply absolute;
  @apply p-3;
  @apply bg-white;
  @apply right-0;
  @apply shadow-lg;
  @apply rounded-xl;
  @apply flex;
  @apply flex-col;
  @apply border-2;
  @apply border-grey_light;
}

.button {
  @apply w-full;
  @apply hover:bg-grey_light;
  @apply p-2;
  @apply rounded-lg;
}
</style>
