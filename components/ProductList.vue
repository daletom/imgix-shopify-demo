<script setup lang="ts">
const props = defineProps({
  products: {
    type: undefined,
    required: true
  }
})
</script>

<template>
  <div class="flex my-20">
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
</template>