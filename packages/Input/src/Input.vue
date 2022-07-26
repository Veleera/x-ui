<template>
  <input
    :type="type"
    class="x-input"
    :class="{ 'x-input-disable': disable }"
    :placeholder="placeholder"
    :disabled="disable"
    :value="value"
    @input="handleInput"
  />
</template>

<script>
export default {
  name: "x-input",
};
</script>
<script setup>
import { defineProps, toRefs,defineEmits } from "vue";
const props = defineProps({
  placeholder: {
    type: String,
    default: "",
  },
  type: {
    type: String,
    default: "text",
    // validator(value) {
    //   return ['text','password','textarea'].includes(value);
    // }
  },
  disable: {
    type: Boolean,
    default: false,
  },
  value:{
    type:String
  },
});
const { placeholder, type, disable,value } = toRefs(props);
const emit = defineEmits({
  input:null
})
const handleInput = (e) => {
  console.log(e.target.value);
  emit('input',e.target.value);
}
</script>

<style lang="scss" src="../style/Input.scss" scoped></style>
