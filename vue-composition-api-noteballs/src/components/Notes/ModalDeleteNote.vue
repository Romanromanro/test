<template>
  <div class="modal is-active">
    <div class="modal-background"></div>
    <div class="modal-card">
      <header class="modal-card-head">
        <p class="modal-card-title">Delete Note?</p>
        <button @click="closeModal" class="delete" aria-label="close"></button>
      </header>
      <section class="modal-card-body">
       Are u sure?
      </section>
      <footer class="modal-card-foot is-justify-content-flex-end">
        <button class="button"
                @click="closeModal"
          >Cancel
        </button>
        <button class="button is-danger">Delete</button>
      </footer>
    </div>
  </div>
</template>

<script setup>


const props = defineProps({
    modelValue: {
      type: Boolean,
      default: false
    }
})

const emit = defineEmits(['update:modelValue'])

const closeModal = () => {
  emit('update:modelValue', false)
}
</script>