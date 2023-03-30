<template>
  <router-view />
</template>

<script>
export default {
  name: "app",
  watch: {
    $route: {
      immediate: true,
      handler(to) {
        document.title = `ЭДО ${to.meta.title || ""}`;
      },
    },
  },
};
</script>
