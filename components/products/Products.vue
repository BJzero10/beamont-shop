<template>
  <div class="flex flex-wrap items-center justify-center">
    <template v-for="p in products">
      <NuxtLink
        class="card w-72 bg-base-100 shadow-xl bg-white md:mx-4 mx-2 mb-4"
        :to="`/products/${p.id}`"
      >
        <figure>
          <img :src="p.image" alt="Shoes" class="w-96 h-48" />
        </figure>
        <div class="card-body">
          <h2 class="card-title text-black font-semibold">
            {{ p.name }}
            <!-- <div class="badge badge-secondary">NEW</div> -->
          </h2>
          <h3 class="text-black/60">{{ $formatMoney(p.price) }}</h3>
          <p></p>
          <div class="card-actions justify-end">
            <template v-for="t in p.tags">
              <div class="badge badge-outline shadow-lg">
                <p class="text-black">{{ t }}</p>
              </div>
            </template>
            <!-- <div class="badge badge-outline">{{t}}</div> -->
          </div>
        </div>
      </NuxtLink>
    </template>
  </div>
</template>

<script>
export default {
  props: {
    products: Array,
  },
};
</script>

<style scoped></style>
