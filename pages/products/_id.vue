<template>
  <div class="bg-white">
    <Nav />
    <div v-if="product">
      <!-- <ProductPerfil :product="product" /> -->
      <div class="w-full md:px-32 py-10 px-8">
        <h1 class="text-center text-2xl text-black font-bold">
          {{ product.name }}
        </h1>
        <!-- <div class="rating rating-lg rating-half">
      <input type="radio" name="rating-10" class="rating-hidden" />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-1"
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-2"
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-1"
        :checked=""
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-2"
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-1"
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-2"
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-1"
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-2"
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-1"
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-2"
      />
    </div> -->
        <div class="flex mt-3 justify-center m-auto">
          <template v-for="t in product.tags">
            <div class="badge badge-outline shadow-lg mx-1">
              <p class="text-black">{{ t }}</p>
            </div>
          </template>
        </div>
        <figure>
          <img
            :src="product.image"
            :alt="product.name"
            class="w-[500px] h-[300px] mt-3 mx-auto rounded-3xl"
          />
        </figure>
        <div class="flex">
          <p class="text-black w-[500px] mx-auto text-justify mt-3">
            {{ product.description }}
          </p>
        </div>
        <div class="flex">
          <button
            @click="$store.commit('cart/AddToCart', product)"
            class="btn btn-primary mx-auto mt-3"
          >
            Agregar al carrito
          </button>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
// import ProductPerfil from "../../components/products/producto/ProductPerfil.vue";
export default {
  async created() {
    const p = await this.$content("products")
      .where({ id: parseInt(this.$route.params.id) })
      .limit(1)
      .fetch();
    this.product = p[0];
  },
  data() {
    return {
      product: null,
    };
  },
  // components: { ProductPerfil },
};
</script>

<style></style>
