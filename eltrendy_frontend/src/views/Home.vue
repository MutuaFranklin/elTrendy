<template>
 <div class="home">
    <section class="hero is-medium is-dark mb-6">
        <div class="hero-body has-text-centered">
            <p class="title mb-6">
                Welcome to elTrendy
            </p>
            <p class="subtitle">
                The best online ladies wear store
            </p>
        </div>
    </section>

    <div class="columns is-multiline">
      <div class="column is-12">
          <h6 class="is-size-4 has-text-centered">Latest products</h6>
      </div>

      <!-- <ProductBox 
        v-for="product in latestProducts"
        v-bind:key="product.id"
        v-bind:product="product" /> -->
      <div class="column is-3" v-for="product in latestProducts" v-bind:key="product.id">
        <div class="box">
          <figure class="image mb-4">
            <img v-bind:src="product.get_thumbnail" alt="">
          </figure>
          <h6 class="is-size-5">{{product.name}}</h6>
          <p class="is-size-6 has-text-grey">${{product.price}}</p>

          <router-link v-bind:to="product.get_absolute_url" class="button is-dark mt-4">View details</router-link>

        </div>

      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Home',
  data(){
    return{
      latestProducts:[]
    }
  },
  components: {
  },
  mounted(){
    this.getLatestProducts()
  },
  methods:{
    getLatestProducts(){
      axios
            .get('/api/v1/latest-products/')
            .then(response => {
              this.latestProducts = response.data
              // console.log(response)
            })
            .catch(error =>{
              console.log(error)
            }) 
    }
  }
}
</script>

<style scoped>
.image{
  margin-top: -1.25em;
  margin-left: -1.25em;
  margin-right: -1.25em;

}

img{
  height: 400px;
}

</style>


