<template>
  <div class="max-w-lg">
    <FormLabel :label="label" name:="name"/>
    <div class="relative flex items-start">
      <div class="flex items-center h-5">
        <input
          :id="name"
          :name="name"
          type="checkbox"
          class="form-checkbox h-4
        w-4 text-indigo-600 transition duration-150 ease-in-out"
        />
      </div>
      <div class="ml-3 text-sm leading-5">
        <p class="text-gray-500">
          Does Real Estate Commission apply?
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import FormLabel from "./FormLabel";
export default {
  name: "FormCheckBox",
  components: { FormLabel },
  props: {
    label: String,
    modelValue: String,
    name: String
  }
};
</script>
