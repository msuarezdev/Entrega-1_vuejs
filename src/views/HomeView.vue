<template>
  <div class="home">
    <navbar />
    <carousel />
    <products />
  </div>
</template>

<script>

import navbar from '@/components/nav-bar.vue'
import carousel from '@/components/HCarousel.vue'
import products from '@/components/Products.vue'


export default {
  name: 'HomeView',
  components: {
    navbar,
    carousel, 
    products,
  }
}
</script>
