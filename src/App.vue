<template>
  <h4>name：{{ testName }}</h4>
  <h4>count：{{ computeCount }}</h4>
  <button @click="changeName">changeTestValue</button>
  <Child :childName="childName" @updateChildName="updateChildName" />
</template>

<script setup>
import { reactive, toRefs, computed, watch } from "vue";
import Child from "./components/child.vue";
const state = reactive({
  testName: "test",
  count: 1,
  childName: "child",
});

const computeCount = computed(() => {
  return state.count * 2;
});

watch(
  () => computeCount.value,
  (newValue, oldValue) => {
    console.log(newValue);
    console.log(oldValue);
  }
);

const changeName = () => {
  state.testName = "tested";
  state.count = 2;
};

const updateChildName = (val) => {
  state.childName = val;
};

const { testName, childName } = toRefs(state);
</script>

<style></style>
