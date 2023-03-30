<template>
  <div>
    <CartStatus :status="'Ожидает оплаты'" />
  </div>
</template>

<script>
import CartStatus from "@/components/common/CartStatus.vue";
export default {
  components: {
    CartStatus,
  },
};
</script>
