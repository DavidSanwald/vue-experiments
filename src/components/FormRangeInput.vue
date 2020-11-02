<template>
  <div>
    <FormLabel :name="name" :label="label" />
    <div class="mt-1 relative rounded-md shadow-sm">
      <div
        class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none"
      ></div>
      <input
        :id="name"
        :name="name"
        type="number"
        class="form-input block w-full pl-7 pr-12 sm:text-sm sm:leading-5"
        placeholder="0.00"
        min="0"
        max="100"
        step="1"
        aria-describedby="price-currency"
        :value="modelValue"
        v-on:input="$emit('update:modelValue', $event.target.value)"
      />
      <div
        class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none"
      >
        <span class="text-gray-500 sm:text-sm sm:leading-5" id="price-currency">
          %
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import FormLabel from "./FormLabel";
export default {
  name: "FormRangeInput",
  components: { FormLabel },
  props: {
    label: String,
    name: String,
    modelValue: String
  }
};
</script>
