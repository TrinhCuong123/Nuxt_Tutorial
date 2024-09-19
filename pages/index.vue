<template>
  <div>
    <p>Using text interpolation: {{ rawHtml }}</p>
    <p>Using v-html directive: <span v-html="rawHtml"></span></p>
    <!-- <div v-bind:id="">hello</div> -->
    <button :disabled="isButtonDisabled">Button</button>
    <div v-bind="objectOfAttrs">hehe</div>
    <div>
    <a v-on:[eventName]="doSomething">Click me</a>
    <input v-model="eventName" placeholder="Enter event name" />
  </div>
  </div>
</template>
<script setup lang="ts">
  const rawHtml = "Xin chào mọi người nè hihi"
  const id = null
  const isButtonDisabled = false
  const objectOfAttrs = {
  id: 'container',
  class: 'wrapper',
  style: 'background-color:yellow'
}
const eventName = ref('click');

const doSomething = () => {
  alert('Link was clicked!');
};
</script>