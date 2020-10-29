<template>
  <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
    <HypoForm msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import HypoForm from "./components/HypoForm.vue";
import { useClient } from "villus";

export default {
  name: "App",
  setup() {
    useClient({
      url: "https://hypofriend.tech/q/"
    });
  },
  components: {
    HypoForm
  }
};
</script>
