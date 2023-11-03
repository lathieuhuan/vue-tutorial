<script setup>
import { ref } from "vue";

const props = defineProps({
  modelValue: String,
  modelModifiers: { default: () => ({}) },
});

const emit = defineEmits(["update:modelValue"]);

// const value = ref('');

// const modelValue = "lasdlas";

function emitValue(e) {
  let value = e.target.value;
  if (props.modelModifiers.doubled) {
    value = value + value;
  }
  emit("update:modelValue", value);
}
</script>

<template>
  <input :value="modelValue" @input="emitValue" />
  <!-- <p>{{ props.errorMessage }}</p> -->
</template>

<style scoped>
/* input {
} */
</style>
