<template>
  <div
      class="card p-4 mb-5"
      :class="`has-background-${bgColor}-dark`"
  >
    <label
        class="label has-text-white"
        v-if="label"
    >
      Label text
    </label>
    <div class="field">
      <div class="control">
       <textarea
           :placeholder="placeholder"
           :value="props.modelValue"
           @input="$emit('update:modelValue', $event.target.value)"
           ref="textareaRef"
           class="textarea"
           v-autofocus
           maxlength="100"
       />
      </div>
    </div>
    <div class="field is-grouped is-grouped-right">
      <div class="control">
        <slot name="buttons"/>
      </div>
    </div>
  </div>
</template>

<script setup>

import {ref} from "vue"
import { vAutofocus } from "@/diractives/vAutofocus"

const props = defineProps({
  modelValue: {
    type: String,
    required: true
  },
  bgColor: {
    default: "success"
  },
  placeholder: {
    type: String,
    default: 'Type something...'
  },
  label: {
    type: String,

  }
});

const emit = defineEmits(['update:modelValue'])

const textareaRef = ref(null)

const focusTextarea = () => {
  textareaRef.value.focus()
}
defineExpose({
  focusTextarea
})


</script>
