<template>
  <button
    class="x-button"
    :class="[`x-button-${type}`, { 'x-button-disable': disable }]"
    @click="handleClick"
    :disabled="disable"
  >
    <span>
      <slot></slot>
    </span>
  </button>
</template>
<script>
export default {
  name: "x-button",
};
</script>
<script setup>
import { defineProps, toRefs, defineEmits } from "vue";

const props = defineProps({
  type: {
    type: String,
    validator(value) {
      // 这个值必须与下列字符串中的其中一个相匹配
      return ["primary", "warning", "danger"].includes(value);
    },
  },
  disable: {
    type: Boolean,
    default: false,
  },
});
const { type, disable } = toRefs(props);
const emit = defineEmits({
  click: null,
});
const handleClick = (e) => {
  emit("click", e);
};
</script>

<style lang="scss" scoped src="../style/Button.scss"></style>
