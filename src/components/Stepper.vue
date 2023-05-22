<template>
  <div class="stepper">
    <div v-for="(step, idx) in props.steps" class="step">
      <div
        :class="['stepProgress', idx + 2 <= activeStep && 'activeStepProgress']"
        v-if="idx !== props.steps.length - 1"
      ></div>
      <div :class="['stepNumber', idx + 1 <= activeStep && 'activeStepName']">
        {{ idx + 1 }}
      </div>
      <div class="stepName">
        {{ step.title }}
      </div>
    </div>
  </div>
  <div class="stepperControls">
    <button @click="goPrev()">Previous</button>
    <button @click="goNext()">Next</button>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

function goPrev() {
  if (activeStep.value <= 1) {
    return;
  }
  activeStep.value--;
}

function goNext() {
  if (activeStep.value >= props.steps.length) {
    return;
  }
  activeStep.value++;
}

interface Props {
  steps: { title: string }[];
}

const props = defineProps<Props>();
const activeStep = ref(1);
</script>

<style scoped>
.stepper {
  display: flex;
}

.step {
  position: relative;
}

.stepName {
  position: absolute;
  top: 40px;
  left: 0;
}

.stepNumber {
  z-index: 1;
  background-color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 2px solid #aaa;
  width: 30px;
  height: 30px;
  margin-right: 65px;
  transition: all 0.5s ease;
}

.stepProgress {
  z-index: -1;
  top: 15px;
  position: absolute;
  width: 100px;
  height: 4px;
  border-top: 4px solid #aaa;
  transition: all 1s ease;
}

.activeStepName {
  border-color: #0ab;
  color: #0ab;
}

.activeStepProgress {
  border-color: #0ab;
  color: #0ab;
}

.stepperControls {
  margin-top: 40px;
  height: 100px;
}

.stepperControls button {
  margin-right: 10px;
  padding: 10px 20px;
  border-radius: 5px;
  border-color: #0ab;
  background-color: #0ab;
  color: white;
}
</style>
