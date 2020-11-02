<template>
  <div class="max-w-lg">
    <FormLabel :label="label" />
    <div class="relative flex items-start">
      <div class="flex items-center h-5">
        <input
          id="comments"
          type="checkbox"
          class="form-checkbox h-4 w-4 text-indigo-600 transition duration-150 ease-in-out"
        />
      </div>
      <div class="ml-3 text-sm leading-5">
        <p class="text-gray-500">
          Get notified when someones posts a comment on a posting.
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormCheckBox",
  props: {
    label: String,
    modelValue: String
  }
};
</script>
