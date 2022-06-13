<template>
  <div class="w-full">
    <template v-for="(c, i) in compras">
      <div class="flex mb-3 sm:px-6 px-0 hover:bg-black/5">
        <figure>
          <img :src="c.product.image" :alt="c.product.name" class="w-80 h-56" />
        </figure>
        <div class="ml-5 mt-2 w-5/6">
          <h2 class="text-black font-bold">
            {{ c.product.name }} x {{ c.quantity }}
          </h2>
          <h3 class="text-black/60">
            {{ $formatMoney(c.product.price * c.quantity) }}
          </h3>
          <div class="flex items-center">
            <button
              class="rounded-full w-6 h-6 bg-indigo-500 hover:bg-indigo-700 mr-5"
              @click="$store.commit('cart/DecreaseItemCount', i)"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="24"
                height="24"
                style="fill: rgb(255, 255, 255); transform: ; msfilter: "
              >
                <path d="M5 11h14v2H5z"></path>
              </svg>
            </button>
            <span class="text-black">{{ c.quantity }}</span>
            <button
              class="rounded-full w-6 h-6 bg-indigo-500 hover:bg-indigo-700 ml-5"
              @click="$store.commit('cart/IncreaseItemCount', i)"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="24"
                height="24"
                style="fill: rgb(255, 255, 255); transform: ; msfilter: "
              >
                <path d="M19 11h-6V5h-2v6H5v2h6v6h2v-6h6z"></path>
              </svg>
            </button>
          </div>
        </div>
        <button
          class="rounded-full bg-indigo-800 h-8 w-8 m-auto hover:bg-indigo-400"
          @click="$store.commit('cart/RemoveCartItem', i)"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="m-auto h-6 w-6"
            style="fill: rgb(255, 255, 255); transform: ; msfilter: "
          >
            <path
              d="M5 20a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8h2V6h-4V4a2 2 0 0 0-2-2H9a2 2 0 0 0-2 2v2H3v2h2zM9 4h6v2H9zM8 8h9v12H7V8z"
            ></path>
            <path d="M9 10h2v8H9zm4 0h2v8h-2z"></path>
          </svg>
        </button></div
    ></template>
  </div>
</template>

<script>
export default {
  props: {
    compras: Array,
  },
};
</script>

<style></style>
