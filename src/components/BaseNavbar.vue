<script lang="ts" setup>
  import Logo from "@/components/MainLogo.vue";

  const links = [
    {
      title: "Home",
      path: "/",
    },
    {
      title: "About",
      path: "/about",
    },
    {
      title: "Community",
      path: "/community",
    },
    {
      title: "Link",
      path: "/link",
    },
  ]
</script>

<template>
    <header class="bg-white w-full py-4 shadow-2xl z-10 relative">
        <div class="flex justify-between items-center container mx-auto">
        <RouterLink to="/">
            <Logo />
        </RouterLink>
        <div class="links">
            <RouterLink
                v-for="link in links"
                :key="link.title"
                class="link-item"
                :to="link.path"
            >
                {{link.title}}
            </RouterLink>
        </div>
        <div class="flex space-x-2">
            <button class="text-accent py-1 px-4">Login</button>
            <button class="text-accent py-1 px-12 rounded-full border border-accent">Play</button>
        </div>
        </div>
  </header>
</template>

<style scoped>
  .links {
    @apply space-x-28 text-gray-500 hidden lg:flex;
  }

  .link-item {
    @apply relative hover:text-gray-600;
  }
  .links .router-link-active {
    @apply text-black;
  }

  .links .router-link-active::before {
    content: '';
    @apply absolute top-7 left-1/2 w-2 h-2 -translate-x-1/2 bg-accent rounded-full;
  }
</style>