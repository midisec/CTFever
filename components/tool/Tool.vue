<template>
  <div @click="!tool.disabled ? $router.push(localePath(tool.route)) : null"
       :class="{'disabled': tool.disabled}"
       class="rounded-lg border border-gray-200 shadow hover:shadow-md transition-all p-4 cursor-pointer flex flex-col justify-between">
    <div>
      <h1 class="text-lg">{{ $t(tool.title) || tool.title }}</h1>
      <p>{{ $t(tool.description) || tool.description }}</p>
    </div>
    <div v-if="tool.tags && tool.tags.length > 0" class="mt-2 text-xs text-gray-400 w-fit" @click.stop>
      <ion-icon class="align-middle -mt-0.5" name="pricetag-outline"></ion-icon>
      <div class="inline-block" v-for="(tag, k) in tool.tags">
        <nuxt-link class="hover:underline" :key="k" :to="`/tag/${tag}`">{{ tag }}</nuxt-link>
        <span v-if="k < tool.tags.length - 1">, </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Tool",
  props: {
    tool: {
      type: Object,
      required: true
    },
  },
}
</script>

<style scoped>
.disabled {
  @apply bg-gray-100 text-gray-600 shadow-none hover:shadow-none cursor-default;
}
</style>
