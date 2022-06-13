<template>
  <div class="bg-white">
    <Nav />
    <div class="w-full md:flex lg:px-24 lg:py-10 md:px-12 py-5 px-6">
      <div v-if="$store.state.cart.cart.length === 0">
        <p>No tiene productos aún, necesita comprar</p>
      </div>
      <div v-else class="w-full">
        <Compras :compras="$store.state.cart.cart" />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Compras from "../../components/cart/Compras.vue";
export default { components: { Compras } };
</script>

<style></style>
