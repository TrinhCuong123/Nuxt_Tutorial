<template>
    <div class="radio-group">
      <RadioButton v-model="selectedOption" inputId="option1" value="Option 1" stype="border-color: #3498db;"/>
      <label for="option1" class="radio-label">Option 1</label>
      <RadioButton v-model="selectedOption" inputId="option2" value="Option 2" stype="border-color: #3498db;"/>
      <label for="option2" class="radio-label">Option 2</label>
    </div>
</template>
  
<script setup>
  import { ref } from 'vue';
  import RadioButton from 'primevue/radiobutton';
  
  const selectedOption = ref(null);
  </script>
  
  <style scoped>
  /* Thay đổi màu của RadioButton */
  .radio-group .p-radiobutton-box {
    border-color: #3498db; /* Màu viền */
  }
  
  .radio-group .p-radiobutton-box .p-radiobutton-icon {
    background-color: #3498db; /* Màu của dấu chấm khi được chọn */
  }
  
  .radio-group .p-radiobutton-box.p-highlight {
    border-color: #3498db; /* Màu viền khi được chọn */
    background-color: #3498db; /* Màu nền khi được chọn */
  }
  
  .radio-group .p-radiobutton-box:hover {
    border-color: #2980b9; /* Màu viền khi hover */
  }
  </style>
  