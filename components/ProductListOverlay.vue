<script setup lang="ts">
const props = defineProps({
  products: {
    type: undefined,
    required: true
  }
})
</script>

<template>
  <div class="bg-white">
    <div class="max-w-2xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
      <div class="mt-8 grid grid-cols-1 gap-y-12 sm:grid-cols-2 sm:gap-x-6 lg:grid-cols-4 xl:gap-x-8">
        <ProductCard
      v-for="product in products"
      :key="product.node.id"
      :image="`https://ix-shopify.imgix.net` + product.node.images.edges[0].node.src.slice(52, -13) + '?auto=format,enhance&w=500&h=500&fit=fill&fill-color=white&trim=auto'"
      :title="product.node.title"
      :price="`${product.node.priceRange.maxVariantPrice.amount}0`"
      :link="`/products/${product.node.handle}`"
      :description="product.node.description"
    />
      </div>
    </div>
  </div>
</template>