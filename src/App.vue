<script lang="ts" setup>
  import Logo from "@/components/MainLogo.vue";
</script>

<template>
  <header class="bg-white w-full py-4 shadow-md">
    <div class="flex justify-between items-center container mx-auto">
      <Logo />
      <div class="flex space-x-28 text-gray-500">
        <RouterLink class="relative hover:text-gray-600" to="/">Home</RouterLink>
        <RouterLink class="relative hover:text-gray-600" to="/about">About</RouterLink>
        <RouterLink class="relative hover:text-gray-600" to="/community">Community</RouterLink>
        <RouterLink class="relative hover:text-gray-600" to="/link">Link</RouterLink>
      </div>
      <div class="flex space-x-2">
        <button class="text-accent py-1 px-4">Login</button>
        <button class="text-accent py-1 px-12 rounded-full border border-accent">Play</button>
      </div>
    </div>
  </header>
  <RouterView />
</template>

<style scoped>
  .router-link-active {
    @apply text-black;
  }

  .router-link-active::before {
    content: '';
    @apply absolute top-6 left-0 w-2 h-2 translate-x-[200%] bg-accent rounded-full;
  }
</style>
