<template>
  <form :class="$style.order">
    <div :class="$style.header"></div>
    <div :class="$style.content">
      <div v-if="type === 'delivery'">
        <div></div>
        <div :class="$style.callme">
          Перезвонить за 1,5 часа до<br />
          предпологаемого времени доставки
        </div>
        <div></div>
      </div>
      <div v-else-if="type === 'takeaway'">
        <div></div>
        <div :class="$style.callme">
          Перезвонить за 1,5 часа до<br />
          предпологаемого времени доставки
        </div>
        <div></div>
      </div>
      <div v-else-if="type === 'stay'">
        <div></div>
        <div :class="$style.callme">
          Перезвонить за 1,5 часа до<br />
          предпологаемого времени доставки
        </div>
        <div></div>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      type: "delivery",
    };
  },
  // уточнить по символам * и #
};
</script>

<style lang="scss" module>
.order {
  border-radius: 0.5rem;
  .header {
    background-color: $bg-secondary;
    padding: 1rem 1.5rem;
  }
  .content {
    background-color: $bg-primary;
    padding: 1.5rem;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 1.5rem;
    .callme {
      color: $t-secondary;
      @include Body3;
      padding: 0.5rem;
      background-color: $bg-secondary;
      border-radius: 0.25rem;
    }
  }
}
</style>
