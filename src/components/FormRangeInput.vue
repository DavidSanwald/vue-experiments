<template>
  <div>
    <label
      for="price"
      class="block text-sm font-medium leading-5 text-gray-700 text-left"
      >{{ label }}</label
    >
    <div class="mt-1 relative rounded-md shadow-sm">
      <div
        class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none"
      ></div>
      <input
        id="price"
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
export default {
  name: "FormRangeInput",
  props: {
    label: String,
    modelValue: String
  }
};
</script>
