<template>
  <div class="wrapper">
    <slot variant="secondary"></slot>
  </div>
</template>

<style scoped>
:slotted(.primary) {
  color: green;
}
</style>
