<template>
  <div id="wrapper">
    <nav class="navbar is-dark">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item"
          ><strong>elTrendy</strong></router-link
        >
        <a
          aria-label="menu"
          aria-expanded="false"
          class="navbar-burger"
          data-target="navbar-menu"
          @click="showMobileMenu = !showMobileMenu"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>
      <div class="navbar-menu" id="navbar-menu" v-bind:class="{'is-active':showMobileMenu}">
        <div class="navbar-end">
          <router-link to="/" class="navbar-item">Home</router-link>
          <router-link to="/" class="navbar-item">Clothes</router-link>
          <router-link to="/" class="navbar-item">Bags</router-link>
          <router-link to="/" class="navbar-item">Cosmetics</router-link>
          <router-link to="/" class="navbar-item">Hair</router-link>
          <router-link to="/" class="navbar-item">Fragrance</router-link>

          <div class="nav-items">
            <div class="buttons">
              <router-link to="/login" class="button is-light">Log In</router-link>
              <router-link to="/cart" class="button is-success">
                <span class="icon"><i class="fas fa-shopping-cart"></i></span>
                <span>Cart</span>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </nav>
    <section class="section">
      <router-view />
    </section>
    <footer class="footer">
      <p class="has-text-centered">Copyright (c) 2021</p>
    </footer>
  </div>
</template>

<script>
export default {
  data(){
    return{
      showMobileMenu:false,
      cart:{
        items:[]
      }
    }
  },
  beforeCreate(){
    this.$store.commit('initializeStore')
  },

  mounted(){
    this.cart = this.$store.state.cart
  },
}
</script>

<style lang="scss">
@import "../node_modules/bulma";
.buttons{
  margin: 6px;
}
</style>

