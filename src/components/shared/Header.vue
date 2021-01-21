<template>
  <div>
    <v-app-bar color="deep-purple accent-4" dense dark>
      <v-toolbar-title>trang Shop</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-badge color="error" icon="lens">
        <v-btn icon>
          <v-icon>shopping_cart</v-icon>
        </v-btn>
      </v-badge>
      <div class="dropdown show">
        <a class="btn btn-secondary dropdown-toggle" href="#" role="button" id="dropdownMenuLink" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
        {{getUser || 'no name'}}</a>
        <div class="dropdown-menu" aria-labelledby="dropdownMenuLink">
          <a v-if="!$store.state.isLogin" class="dropdown-item" href="/login">Đăng nhập</a>
          <a v-else class="dropdown-item a" @click="logout" >Đăng xuất</a>
        </div>
      </div>
    </v-app-bar>
  </div>
</template>

<script>
import { mapMutations, mapGetters } from "vuex";
export default {
  methods: {
    ...mapMutations(["setUser", "Cart"]),
    logout(){
      localStorage.removeItem('user')
      window.location.href = '/'
    },
  },
  mounted() {
    this.setUser(),
    this.Cart()
  },
  computed: {
    ...mapGetters(["count", "getUser",])
  }
};
</script>

<style scoped>
.top {
  position: fixed;
  top: 0;
  width: 100%;
  box-sizing: border-box;
  z-index: 1000;
}
.a{
  cursor: pointer;
}
</style>