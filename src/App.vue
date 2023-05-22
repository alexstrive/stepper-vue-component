<script setup lang="ts">
import Stepper from './components/Stepper.vue';
const steps = [
  { title: 'Step 1' },
  { title: 'Step 2' },
  { title: 'Step 3' },
  { title: 'Final' },
];
</script>

<template>
  <Stepper :steps="steps" />
</template>

<style>
:root {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
</style>
