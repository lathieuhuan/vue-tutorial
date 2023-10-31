<script setup>
import { onUpdated, ref, watch, watchEffect } from "vue";

const props = defineProps({
  value: {
    type: String,
    required: true,
  },
});

const value = ref("");

watchEffect(() => {
  console.log("watchEffect input", props.value);
  //   value.value = props.value;
});

watch(
  () => props.value,
  () => console.log("watch input", props.value),
  {
    immediate: true,
  }
);

// watchEffect(() => {
//   console.log("value", value.value);
// });

const emit = defineEmits(["change"]);

function onChange(e) {
  value.value = e.target.value;
  emit("change", value.value);
}
</script>

<template>
  <input :value="value" @input="onChange" />
</template>

<style scoped>
input {
  /* padding: ; */
}
</style>
