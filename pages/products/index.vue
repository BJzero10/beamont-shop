<template>
  <div class="bg-white">
    <Nav />
    <div class="w-full md:flex lg:px-24 lg:py-10 md:px-12 py-5 px-6">
      <div class="lg:w-80 md:w-64 md:block flex flex-col w-full">
        <input
          type="text"
          placeholder="Buscar"
          class="input input-bordered lg:w-80 w-64 max-w-xs bg-white border-indigo-400 mx-auto"
          v-model="search"
        />
        <h3 class="mt-3">Categorias</h3>
        <div class="md:overflow-x-hidden overflow-x-auto scroll-smooth">
          <div class="md:block inline-flex">
            <template v-for="c in categories">
              <div
                class="btn bg-white hover:bg-black/10 border-none flex h-16 items-center py-0"
              >
                <div class="avatar">
                  <div class="w-12 h-12 rounded-full py-0">
                    <img :src="c.image" />
                  </div>
                </div>
                <div class="card-body py-0">
                  <h2 class="text-left capitalize">{{ c.name }}</h2>
                  <!-- <p>Click the button to watch on Jetflix app.</p> -->
                  <!-- <div class="card-actions justify-end">
                  <button class="btn btn-primary">Watch</button>
                </div> -->
                </div>
              </div>
            </template>
          </div>
        </div>
      </div>
      <div class="md:w-3/4 w-full md:mt-0 mt-3">
        <Products :products="filteredProducts" />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Products from "../../components/products/Products.vue";
export default {
  components: { Products },
  async created() {
    this.categories = await this.$content("category").fetch();
    this.products = await this.$content("products").fetch();
  },
  data() {
    return {
      products: null,
      categories: null,
      search: null,
    };
  },
  computed: {
    filteredProducts() {
      if (!this.search || !this.products) return this.products || [];
      return this.products.filter((p) => {
        const s = this.search.toLowerCase();
        const n = p.name.toLowerCase();
        const c = p.tags.toString().toLowerCase();
        console.log(c);
        const price = String(p.price);
        const sprice = p.salePrice ? String(p.salePrice) : "";
        // const r = p.rating.toString();
        const r = String(p.rating);

        return (
          n.includes(s) ||
          c.includes(s) ||
          price.includes(s) ||
          sprice.includes(s) ||
          r.includes(s)
        );
      });
    },
  },
};
</script>

<style></style>
