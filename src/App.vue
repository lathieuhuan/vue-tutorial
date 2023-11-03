<script setup>
import { ref, watchEffect, computed } from "vue";
import Button from "./components/Button.vue";
import Input from "./components/Input.vue";
import Wrapper from "./components/Wrapper.vue";
import VoucherList from "./components/VoucherList.vue";
import { useMouse } from "./composables/useMouse.js";

// const num = ref(0);
const boo = ref(false);
// const text = ref("error");
// const vouchers = ref(["A"]);
// watchEffect(() => console.log(text.value));

const position = computed(() => (boo.value ? "prefix" : "suffix"));
const mouse = useMouse();
</script>

<template>
  <!-- <p>[{{ JSON.stringify(num) }}]</p> -->
  <!-- <input type="text" v-model.trim="num" /> -->

  <!-- <component :is="boo ? Button : Input">Hello</component> -->
  <!-- <Input v-model.doubled="text" /> -->
  <!-- <Input :value="text" :errorMessage="text" @change="console.log" /> -->

  <p>{{ mouse.x }} {{ mouse.y }}</p>

  <Wrapper v-slot="props">
    <Button :class="props.variant" @click="boo = !boo">
      Click {{ position }}
      <template #prefix><span>Icon</span></template>
    </Button>
  </Wrapper>
  <!-- <VoucherList v-model:vouchers="vouchers" v-model:merchants="merchants" /> -->
</template>
