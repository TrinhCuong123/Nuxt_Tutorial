<template>
  <Dialog :visible="visible" @hide="emitHide">
    <template #header>
      <h3>My Dialog</h3>
    </template>
    <template #default>
      <!-- Nội dung Dialog -->
      <p>Đây là nội dung của Dialog</p>
    </template>
    <template #footer>
      <Button label="Lưu" @click="emitSave" />
      <Button label="Đóng" @click="emitHide" />
    </template>
  </Dialog>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'
import Dialog from 'primevue/dialog'
import Button from 'primevue/button'

const props = defineProps({
  visible: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['hide', 'save'])

const emitHide = () => {
  emit('hide')
}

const emitSave = () => {
  emit('save')
}
</script>

<style scoped>
/* Thêm CSS tùy chỉnh nếu cần */
</style>
