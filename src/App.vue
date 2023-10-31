<script setup>
import { ref, watch, watchEffect } from "vue";
import Input from "./components/Input.vue";
import Wrapper from "./components/Wrapper.vue";

const childValue = ref("");

watch(childValue, () => console.log("watch app", childValue.value), {
  immediate: true,
});

watchEffect(() => console.log("watchEffect app", childValue.value));
</script>

<template>
  <p>Child value: {{ childValue }}</p>
  <Wrapper>
    <Input
      #test
      :value="childValue + childValue"
      @change="
        (newValue) => {
          childValue = newValue;
        }
      "
    />
    <p>Hello</p>
  </Wrapper>
</template>
