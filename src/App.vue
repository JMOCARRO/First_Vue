<template>
  <div id="app">
    
    <div class="product">
            
            <div class="product-image">

                <img :title="imtitle" v-bind:src="image">
                
            </div>
            <div class="product-info">
                <h1> {{ product }} </h1>
                <p> {{description + " "+ product}}</p>
                <h2> The name of the product is: {{product}}</h2>
                <p v-if="inventory>10">In Stock</p>
                <p v-else-if="inventory<=10 && inventory>0">Stock running low</p>
                <p v-else>Out of Stock</p>
                <p v-show="onSale">On SALE</p>


                <ul>
                    <li v-for="detail in details" :key="detail"> {{ detail }}</li>
                </ul>
                <div v-for="variant in variants" :key="variant.item">
                    <p v-on:mouseover="updateProduct(variant.vImage)">{{ variant.iColour }}</p>
                </div>

                <P>
                    <a :href="imsrc" target="_blank">Image Source</a>
                </P>

                <div class="container">
                  <div class="row">
                    <div class="col">
                      <b-button variant="primary" v-on:click="addToCart"> Add to Cart</b-button>
                    </div>
                    <div class="col">
                      <b-button variant="danger" v-on:click="decrementCart"> Remove Cart</b-button>
                    </div>
                    <div class="col">
                      <b-button variant="danger" v-on:click="cart+=1"> Add to Cart</b-button>
                    </div>
                    <div class="col">
                      <div class="cart">
                          <h4><b-badge variant="info">Cart({{cart}})</b-badge></h4>
                      </div>
                    </div>
                  </div>
                </div>

            </div>
            
        </div>
    
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    //HelloWorld
  },
  data() {
    return {
      product: 'Socks',
      description: "Nice new blue socks",
      image: 'droplet2.jpg',
      imtitle: "Nice Droplet",
      imsrc: "https://www.w3schools.com",
      inventory: 100,
      onSale:true,
      details:["nice","tall","glorious"],
      variants:[{item:"list1", iColour:"Droplet",vImage:"droplet2.jpg"},{item:"list2", iColour:"Beach",vImage:"Jim Beach.jpg"}],
      cart:0
    };
  },
    methods:{

        addToCart: function (){
            this.cart+=1
        },
        decrementCart: function (){
            this.cart+=-1
        },
        updateProduct: function(x){
            this.image=x
        }
    }
}
</script>

<style> 


body {
    font-family: tahoma;
    color: #282828;
    margin: 0px;
  }
  
  .nav-bar {
    background: linear-gradient(-90deg, #84CF6A, #16C0B0);
    height: 60px;
    margin-bottom: 15px;
  }

  .product {
    display: flex;
    flex-flow: wrap;
    padding: 1rem;
  }

  img {
    border: 1px solid #d8d8d8;
    width: 70%;
    margin: 40px;
    box-shadow: 0px .5px 1px #d8d8d8;
  }
  
  .product-image {
    width: 80%;
  }
  
  .product-image,
  .product-info {
    margin-top: 10px;
    width: 50%;
  }
  
  .color-box {
    width: 40px;
    height: 40px;
    margin-top: 5px;
  }
  
  /*
  .cart {
    margin-right: 25px;
    float: right;
    border: 1px solid #d8d8d8;
    padding: 5px 20px;
  }
  */
  /*
  button {
    margin-top: 30px;
    border: none;
    background-color: #1E95EA;
    color: white;
    height: 40px;
    width: 120px;
    font-size: 12px;
    margin: 10px;
  } 
  */

  .disabledButton {
    background-color: #d8d8d8;
  }
  
  .review-form {
    width: 400px;
    padding: 20px;
    margin: 40px;
    border: 1px solid #d8d8d8;
  }
  
  input {
    width: 100%;  
    height: 25px;
    margin-bottom: 20px;
  }
  
  textarea {
    width: 100%;
    height: 60px;
  }

  .tab {
    margin-left: 20px;
    cursor: pointer;
  }

  .activeTab {
    color: #16C0B0;
    text-decoration: underline;
  }
  

</style>
