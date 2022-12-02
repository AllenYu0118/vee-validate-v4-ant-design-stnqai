<template>
  <a-form-item
    :label="label"
    :has-feedback="!!errorMessage"
    :help="errorMessage"
    :validate-status="errorMessage ? 'error' : undefined"
  >
    <a-input v-model:value="value" :type="type" />
  </a-form-item>
</template>

<script setup lang="ts">
import { toRef } from 'vue';
import { useField } from 'vee-validate';

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  label: {
    type: String,
    required: true,
  },
  type: {
    type: String,
    required: true,
  },
});

const { errorMessage, value } = useField(toRef(props, 'name'));
</script>
