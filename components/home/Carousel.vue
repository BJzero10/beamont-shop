<template>
  <!-- <v-carousel>
      <template #prev="{attrs, on}">
        <v-btn v-bind="attrs" v-on="on">
            <v-icon>mdi-arow-left</v-icon>
        </v-btn>
      </template>
      <template #next="{attrs, on}">
        <v-btn v-bind="attrs" v-on="on">
            <v-icon>mdi-arow-right</v-icon>
        </v-btn>
      </template>
  <v-carousel-item v-for="(p, i) in sale_items" :key="`saleItem-${i}`">
    <v-image :src="p.image">
    
    </v-image>
  </v-carousel-item>
  </v-carousel> -->
  <div class="carousel w-full">
    <template v-for="(p, i) in sale_items">
      <div :id="'slide' + i" class="carousel-item relative w-full">
        <img :src="p.image" class="w-full h-[650px]" />
        <div
          class="card w-[550px] h-80 bg-white/80 absolute -translate-y-1/2 left-36 top-1/2 md:visible invisible"
        >
          <div class="card-body">
            <h2 class="card-title text-3xl font-bold text-black">
              {{ p.name }}
            </h2>
            <h3 class="text-xl font-normal text-indigo-600">
              {{ $formatMoney(p.price) }}
            </h3>
            <p class="text-black text-justify">{{ p.description }}</p>
            <div class="card-actions justify-end">
              <NuxtLink :to="`/products/${p.id}`" class="btn btn-primary">
                Visitar
              </NuxtLink>
            </div>
          </div>
        </div>
        <template v-if="i > 0 && i < sale_items.length - 1">
          <div
            class="absolute flex justify-between transform -translate-y-1/2 left-5 right-5 top-1/2"
          >
            <a :href="'#slide' + (i - 1)" class="btn btn-circle">❮</a>
            <a :href="'#slide' + (i + 1)" class="btn btn-circle">❯</a>
          </div>
        </template>
        <template v-if="i === 0">
          <div
            class="absolute flex justify-between transform -translate-y-1/2 left-5 right-5 top-1/2"
          >
            <a :href="'#slide' + (sale_items.length - 1)" class="btn btn-circle"
              >❮</a
            >
            <a :href="'#slide' + (i + 1)" class="btn btn-circle">❯</a>
          </div>
        </template>
        <template v-if="i === sale_items.length - 1">
          <div
            class="absolute flex justify-between transform -translate-y-1/2 left-5 right-5 top-1/2"
          >
            <a :href="'#slide' + (i - 1)" class="btn btn-circle">❮</a>
            <a :href="'#slide' + 0" class="btn btn-circle">❯</a>
          </div>
        </template>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  props: {
    sale_items: Array,
  },
};
</script>

<style></style>
