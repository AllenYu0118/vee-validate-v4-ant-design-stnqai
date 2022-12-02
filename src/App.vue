<template>
  <Form :validation-schema="schema" @submit="onSubmit">
    <!-- You can use the field component to wrap a q-* component -->
    <!-- Do this if you have only one or a few places that need validation -->
    <Field name="fullName" v-slot="{ value, handleChange, errorMessage }">
      <a-form-item
        label="Full name"
        :has-feedback="!!errorMessage"
        :help="errorMessage"
        :validate-status="errorMessage ? 'error' : undefined"
      >
        <a-input :value="value" @update:value="handleChange" />
      </a-form-item>
    </Field>

    <!-- You can use the field component to wrap a q-* component -->
    <!-- Do this if you have only one or a few places that need validation -->
    <Field name="email" v-slot="{ value, handleChange, errorMessage }">
      <a-form-item
        label="Email"
        :has-feedback="!!errorMessage"
        :help="errorMessage"
        :validate-status="errorMessage ? 'error' : undefined"
      >
        <a-input :value="value" @update:value="handleChange" />
      </a-form-item>
    </Field>

    <!-- Or compose vee-validate's validation into your q-* components -->
    <!-- Do this if you plan to have validation frequently throughout your app -->
    <AntInputWithValidation name="password" label="Password" type="password" />

    <Area name="area" />

    <a-form-item>
      <a-button type="primary" html-type="submit">Submit</a-button>
    </a-form-item>
  </Form>
</template>

<script lang="ts" setup>
import { defineComponent, ref } from 'vue';
import { Field, Form } from 'vee-validate';
import * as yup from 'yup';
import AntInputWithValidation from './components/AntInputWithValidation.vue';
import Area from './components/Area.vue';

const area = ref({
  area: null,
  unit: 1,
});

const schema = yup.object({
  email: yup.string().required().email().label('Email address'),
  fullName: yup.string().required().label('Full name'),
  password: yup.string().required().min(6).label('Password'),
  area: yup.string().required().min(6).label('area'),
});

const onSubmit = (values) => {
  console.log('Success:', values);
};
</script>
