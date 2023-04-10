<template>
  <div :class="$style.container">
    hello world
  </div>
</template>

<!-- <script>
import CreateOrder from "@/components/common/CreateOrder.vue";
export default {
  components: {
    CreateOrder,
  },
};
</script> -->

<style lang="scss" module>
.container {
  @include container;
}
</style>
