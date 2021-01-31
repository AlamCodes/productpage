<template>
    <div class="page">
        <div class="nav-bar"></div>
    <div class="product">
        <div class="product-image">
            <img :src="image" />
        </div>
        <div class="product-info">
           <h1>{{ title }}</h1> 
           <p v-if="inventory > 10"> In Stock</p>
           <p v-else-if="inventory <= 10 && inventory > 0">Almost Sold Out!</p>
           <p v-else>Out of Stock</p>

           <ul>
               <li v-for="detail in details" :key="detail.detailId">{{ detail.detailsInfo }}</li>
           </ul>

           <div v-for="(variant, index) in variants" 
                :key="variant.variantsId"
                 class="color-box"
                 :style="{backgroundColor: variant.variantsColor }"
                  @mouseover="updateImage(index)">
               
           </div>

           <button @click="addToCart"> 
               Add To Cart
           </button>

           <div class="cart">
               <p>cart({{cart}})</p>
           </div>
        </div>
        </div>
    </div>
</template>



<script>
export default {
   data(){
       return{
           brand: 'Nike',
           product: 'Shoes',
           selectedVariants: 0,
          //  image: "https://static.highsnobiety.com/thumbor/eUe8r1r2hREzAyuoDh8Lqy0LK7k=/1600x1067/static.highsnobiety.com/wp-content/uploads/2018/05/21122329/white-nikes-main1.jpg",
           inStock: true,
           inventory: 17,
           details:[
                    {
                        detailsId:1,
                        detailsInfo: "one year warrenty"
                    } ,
                    {
                         detailsId:2,
                        detailsInfo: "Region of origin: vietnam"
                    },
                    {
                        detailsId:3,
                        detailsInfo:  "Nike air max 270G"
                    }       
           
           ],
           variants:[
               {
                   variantsId:1,
                   variantsColor: "grey",
                   variantsImage:  "https://static.highsnobiety.com/thumbor/eUe8r1r2hREzAyuoDh8Lqy0LK7k=/1600x1067/static.highsnobiety.com/wp-content/uploads/2018/05/21122329/white-nikes-main1.jpg",
               },
               {
                   variantsId: 2,
                   variantsColor: "Black",
                   variantsImage:  "https://media.gq-magazine.co.uk/photos/5fd8c7096524743d1adc12a8/master/w_828%2cc_limit/16122020_SU_07.jpg",
               }
           ],
           cart:0
       }
       },

       computed:{
         title(){
           return this.brand + ' '+ this.product
         },
         image(){
           return this.variants[this.selectedVariants].variantsImage
         }
       },

       methods:{
           addToCart: function(){
               this.cart += 1
           },
           updateImage: function(index){
               this.selectedVariants= index
               console.log(index)
           },
       }
      
}
</script>



<style scoped>
 body {
    font-family: tahoma;
    color:#282828;
    margin: 0px;
  }
  
  .nav-bar {
    background: linear-gradient(-90deg, #6aafcf, #164cc0);
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
  
  .cart {
    margin-right: 25px;
    float: right;
    border: 1px solid #d8d8d8;
    padding: 5px 20px;
  }
  
  button {
    margin-top: 30px;
    border: none;
    background-color: #1E95EA;
    color: white;
    height: 40px;
    width: 100px;
    font-size: 14px;
  } 
  
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