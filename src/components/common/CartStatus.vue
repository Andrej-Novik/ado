<template>
  <div :class="[$style.status, $style[color]]">
    <span :class="$style.dot"></span>
    <span :class="$style.test">{{ status }}</span>
  </div>
</template>

<script>
export default {
  props: {
    status: {
      type: String,
      default: "",
    },
  },
  computed: {
    color() {
      let color = "";
      switch (this.status) {
        case "Оплачен":
          color = "green";
          break;
        case "Отложен":
          color = "blue";
          break;
        case "Ожидает оплаты":
          color = "yellow";
          break;
        default:
          color = "";
      }
      return color;
    },
  },
};
</script>

<style lang="scss" module>
.status {
  border-radius: 6.25rem;
  padding: 0.25rem 0.5rem;
  display: inline-flex;
  align-items: center;
  color: $t-primary;

  .dot {
    margin: 0 0.25rem 0 0;
    width: 0.375rem;
    height: 0.375rem;
    border-radius: 50%;
  }
  .text {
    @include Body2;
  }
  &.green {
    background-color: $green-status;
    .dot {
      background-color: $dark-green;
    }
  }
  &.blue {
    background-color: $blue-status;
    .dot {
      background-color: $blue-primary;
    }
  }
  &.yellow {
    background-color: $yellow-status;
    .dot {
      background-color: $yellow;
    }
  }
}
</style>
