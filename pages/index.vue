<template>
  <div class="bg-white">
    <Nav />
    <Carousel :sale_items="sale_items" />
    <div class="w-full px-32 py-10">
      <h2 class="text-3xl font-bold text-black">Nuestros Productos</h2>
      <div class="overflow-x-scroll scroll-smooth">
        <div class="inline-flex items-center justify-center">
          <CardsProducts :products="products" />
        </div>
      </div>
    </div>
    <div class="w-full px-32 py-10">
      <newsletter />
    </div>
    <Footer />
  </div>
</template>

<script>
import Carousel from "../components/home/Carousel.vue";
import CardsProducts from "../components/home/CardsProducts.vue";
import Newsletter from "../components/home/Newsletter.vue";
export default {
  async created() {
    this.sale_items = await this.$content("products")
      .where({ onSale: true })
      .fetch();
    this.products = await this.$content("products").fetch();
  },
  data() {
    return {
      products: null,
      sale_items: null,
    };
  },
  components: { Carousel, CardsProducts, Newsletter },
};
</script>

<style scoped>
/* .scroll-smooth::-webkit-scrollbar {
  display: none;
} */
</style>
