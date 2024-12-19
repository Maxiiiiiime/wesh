<template>
    <div  class="card">
             
             <div class="img-container">
               <img :src="produit.img" />
             </div>
   
             <div class="card-text">
               <h3>{{produit.description}}</h3>
               <span>{{produit.price}}€</span>
             </div>
 
             <div class="card-icons">
               <div class="like-container">
                 <input
                   type="checkbox"
                   :value="produit.id"
                   name="checkbox"
                   :id="produit.id"
        
                 />
                 <label :for="produit.id">
                   <i class="fas fa-heart"  @click="addToLike(produit)"></i>
                 </label>
               </div>
   
               <div class="add-to-cart">
                 <button @click="addToCart(produit)">
                   <i class="fas fa-shopping-cart"></i>
                 </button>
               </div>
             </div>

           </div>
</template>

<script setup>
    import {ref} from 'vue'

    const liked = ref(false)

    const props = defineProps({
        produit: Object
    })

    const emits = defineEmits([
        'addToCart', 'addToLike'
    ])

    const addToCart = (produit) => {
        emits('addToCart', produit)
    }

    const addToLike = (produit) => {
        emits('addToLike', produit)
    }
</script>