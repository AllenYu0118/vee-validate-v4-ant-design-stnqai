<template>
  <a-form-item
    label="車位坪數"
    required
    :auto-link="false"
    :help="errorMessage"
    :validate-status="errorMessage ? 'error' : ''"
  >
    <a-input-group compact class="w-280px! inline-block!">
      <a-input-number
        v-model:value="value"
        class="w-180px!"
        :controls="false"
        maxlength="6"
      />
    </a-input-group>
  </a-form-item>
</template>

<script lang="ts" setup>
import { toRef } from 'vue';
import { useField } from 'vee-validate';

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
});

const { errorMessage, value } = useField(toRef(props, 'name'));

console.log('value', value);
</script>
