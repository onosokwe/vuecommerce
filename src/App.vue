<template>
  <div id="app">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-7 products"> 
          <div class="row">
            <div class="col-sm-6" v-for="product in products" :key="product.id" >
              <product 
                v-on:add-to-cart="addToCart(product)"
                :isInCart="isInCart(product)"
                :product="product">
              </product>
            </div>
          </div>
        </div>
        <div class="col-md-5 cart"> 
          <cart 
            v-on:pay="pay()" 
            v-on:remove-from-cart="removeFromCart($event)" 
            :items="cart">
          </cart>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import products from '@/products.json';
import Product from '@/components/Product.vue';
import Cart from '@/components/Cart.vue';

export default {
  name: 'App',
  components: {
    Product,
    Cart
  },
  data(){
    return {
      products,
      cart: []
    }
  },
  methods: {
    addToCart(product){
      this.cart.push(product)
      console.log(this.cart)
    },
    isInCart(product){
      const item = this.cart.find(item => item.id === product.id)
      if(item){
        return true
      }
      return false
    },
    removeFromCart(product){
      this.cart = this.cart.filter(item => item.id !== product.id)
    },
    pay(){
      this.cart = []
      alert("Done shopping!")
    }
  }
}
</script>

<style>
  body {
    background: #efefef;
  }
  .products {
    background: #e9e9e9;
    padding: 30px;
  }
  .cart {
    background:  #fff;
    padding: 30px;
  }
  .badge {
    margin-top: 3px
  }
</style> 