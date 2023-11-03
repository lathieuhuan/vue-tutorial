<script></script>

<template>
  <button class="primary" @click="console.log('click on child')">
    <slot name="prefix"></slot>
    <slot></slot>
    <slot name="suffix"></slot>
  </button>
</template>

<style>
.primary {
  background-color: black;
  color: white;
}
.btn-md {
  padding: 0.25rem 0.5rem;
}
.btn-lg {
  padding: 0.5rem 1rem;
}
</style>
