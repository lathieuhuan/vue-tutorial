<script setup>
import { ref } from "vue";

const props = defineProps(["vouchers", "merchants"]);
const emit = defineEmits(["update:vouchers", "update:merchants"]);

const input = ref("");
const isVoucher = ref(false);
const vouchers = ref([...props.vouchers]);
const merchants = ref([]);

const addVoucher = () => {
  if (isVoucher.value) {
    vouchers.value.push(input.value);
    emit("update:vouchers", vouchers.value);
  } else {
    merchants.value.push(input.value);
    emit("update:merchants", merchants.value);
  }
  input.value = "";
};
</script>

<template>
  <p>{{ isVoucher ? "Voucher" : "Merchant" }}</p>
  <input v-model="input" />
  <p>
    Child vouchers {{ vouchers.join(", ") }}. Child merchants
    {{ merchants.join(", ") }}
  </p>
  <button @click="isVoucher = !isVoucher">Toggle</button>
  <button @click="addVoucher()">Add</button>
</template>
