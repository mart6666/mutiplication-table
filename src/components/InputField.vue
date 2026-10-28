<script setup>
import {inject} from "vue";

const props = defineProps({
  labelText: {
    type: String,
    required: true,
  },
  inputType: {
    type: String,
    required: false,
    default: "text",
  },
  min: {
    type: String,
    required: false,
  },
})

const model = defineModel()

</script>

<template>
  <section class="input-field">
    <strong>{{ props.labelText }}</strong>
    <input :type="inputType"
           v-model="model" :min="props.min"/>
  </section>
</template>

<style scoped>
section.input-field {
  display: flex;
  gap: 20px;
  justify-content: space-between;
  width: 100%;
  flex-direction: column;

  div {
    border: 1px solid black;
  }

  @media screen and (width > 600px) {
    flex-direction: row
  }
}
</style>