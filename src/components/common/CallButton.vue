<template>
  <button
    :class="[$style.button, { [$style.disabled]: disabled }, $style[color]]"
    :disabled="disabled"
    @click="$emit('click')"
  >
    <img :src="icon" alt="" />
  </button>
</template>

<script>
export default {
  props: {
    icon: {
      type: String,
      default: "",
    },
    color: {
      type: String,
      default: "",
      validator: (value) => ["red", "green"].includes(value),
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" module>
.button {
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  width: 100%;
  outline: 0;
  height: 2.5rem;
  border-radius: 0.25rem;
  transition: all 0.3s ease-in-out;
  border: 1px solid transparent;
  &.red {
    background-color: $red-button;
  }
  &.green {
    background-color: $green-button;
  }

  &.disabled,
  &:disabled {
    pointer-events: none;
  }
  // &:hover {
  //   box-shadow: $primaryShadow;
  // }
}
</style>
