<template>
  <h5>{{ childName }}</h5>
  <button @click="changeChildName">changeChildName</button>
</template>

<script setup>
const props = defineProps({
  childName: {
    type: String,
    default: "",
  },
});

const $emit = defineEmits(["updateChildName"]);
const changeChildName = () => {
  $emit("updateChildName", "RtyXmd");
};
</script>

<style></style>
