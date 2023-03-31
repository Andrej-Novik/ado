<template>
  <form :class="$style.form" @submit.prevent="callPhone">
    <div :class="$style.phone">
      <input
        type="text"
        :placeholder="'(967) 491-85-91'"
        v-model="phoneValue"
        @focus="onPress"
      />
    </div>
    <div :class="$style.steps">
      <div
        v-for="step in steps"
        :key="step.number"
        :class="[$style.step, { [$style.active]: step.isActive }]"
      >
        {{ step.number }}
      </div>
    </div>
    <div :class="$style.container">
      <div v-for="item in values" :key="item" @click="enterValue(item)">
        {{ item }}
      </div>
    </div>
    <CallButton :color="buttunType.color" :icon="buttunType.icon" />
  </form>
</template>

<script>
import CallButton from "@/components/common/CallButton.vue";
export default {
  props: {
    type: {
      type: String,
      default: "green",
      validator: (value) => ["red", "green"].includes(value),
    },
  },
  data() {
    return {
      values: ["1", "2", "3", "4", "5", "6", "7", "8", "9", "*", "0", "#"],
      steps: [
        {
          number: "1",
          isActive: true,
        },
        {
          number: "2",
          isActive: false,
        },
        {
          number: "3",
          isActive: false,
        },
      ],
      phoneValue: "+375",
    };
  },
  computed: {
    buttunType() {
      let type = {
        color: "green",
        icon: "/icons/green-call.svg",
      };
      if (this.type === "red") {
        (type.color = "red"), (type.icon = "/icons/red-call.svg");
      }
      return type;
    },
  },
  components: {
    CallButton,
  },
  methods: {
    enterValue(value) {
      this.phoneValue += value;
    },
    callPhone() {
      this.phoneValue = "+375";
    },
    onPress() {
      const values = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"];
      document.addEventListener("keydown", function (event) {
        if (values.includes(event.key)) {
          this.phoneValue += event.key;
        }
        if (event.key === "Backspace") {
          this.phoneValue = this.phoneValue.slice(0, -1);
        }
      });
    },
  },
};
</script>

<style lang="scss" module>
.form {
  padding: 1rem;
  background-color: $bg-secondary;
  border-radius: 0.5rem;
  width: 18.125rem;
  .phone {
    border-bottom: 1px solid $t-tertiary;
    input {
      width: 100%;
      border: none;
      @include H2;
      height: 3.5rem;
      text-align: center;
      color: $t-secondary;
      &::placeholder {
        @include H2;
        color: $t-secondary;
        text-align: center;
      }
    }
  }
  .steps {
    margin: 0 0 1rem 0;
    display: flex;
    .step {
      @include Subtitle;
      width: 100%;
      height: 1.5rem;
      display: flex;
      justify-content: center;
      align-items: center;
      border-top: 1px solid transparent;
      position: relative;
      top: -1px;
      &.active {
        border-top: 1px solid $t-secondary;
        color: $t-secondary;
      }
    }
  }
  .container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 0.25rem;
    margin: 0 0 1rem 0;
    div {
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      width: 100%;
      height: 3rem;
      background-color: $bg-primary;
      border-radius: 0.25rem;
      border: 1px solid transparent;
      @include H2;
      color: $t-secondary;
    }
  }
}
</style>
