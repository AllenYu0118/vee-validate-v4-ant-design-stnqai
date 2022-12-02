<template>
  <a-form-item
    label="車位坪數"
    required
    :auto-link="false"
    :help="errorMsg"
    :validate-status="errorMsg ? 'error' : ''"
  >
    <a-input-group compact class="w-280px! inline-block!">
      <a-input-number
        v-model:value="houseArea.area"
        class="w-180px!"
        :controls="false"
        maxlength="6"
        @blur="emits('validate', 'area')"
      />
      <a-select
        v-model:value="houseArea.unit"
        class="w-100px!"
        :options="options"
      >
      </a-select>
    </a-input-group>
  </a-form-item>
</template>

<script lang="ts" setup>
import { useVModel } from '@vueuse/core';

const emits = defineEmits(['validate']);
const props = defineProps<{
  modelValue: {
    area: number;
    unit: number;
  };
}>();

const houseArea = useVModel(props, 'modelValue');

const options = [
  {
    label: '坪',
    value: 1,
  },
  {
    label: '平方公尺',
    value: 2,
  },
];
</script>
