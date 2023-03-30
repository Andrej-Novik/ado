<template>
  <div>
    <CallButton :color="'red'" :icon="'./icons/red-call.svg'" />
  </div>
</template>

<script>
import CallButton from "@/components/common/CallButton.vue";
export default {
  components: {
    CallButton,
  },
};
</script>
