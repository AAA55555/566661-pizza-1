<template>
  <div>
    <button
      type="button"
      class="counter__button counter__button--minus"
      :disabled="decrementDisabled"
      @click="$emit('minusCount')"
    >
      <span class="visually-hidden">{{ textBtnFirst }}</span>
    </button>
    <input
      type="text"
      name="counter"
      class="counter__input"
      v-model="count"
      readonly
    />
    <button
      type="button"
      class="counter__button counter__button--plus"
      @click="$emit('plusCount')"
      :disabled="!incrementDisabled"
    >
      <span class="visually-hidden">{{ textBtnSecond }}</span>
    </button>
  </div>
</template>

<script>
export default {
  name: "ItemCounter",
  props: {
    textBtnFirst: {
      type: String,
      default: "Меньше",
    },
    textBtnSecond: {
      type: String,
      default: "Больше",
    },
    count: {
      type: Number,
      default: 0,
    },
    maxCount: {
      type: Number,
      default: 3,
    },
    minCount: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    decrementDisabled() {
      return this.count === this.minCount;
    },
    incrementDisabled() {
      return this.count < this.maxCount;
    },
  },
};
</script>

<style scoped></style>
