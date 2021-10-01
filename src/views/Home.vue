<template>
  <div class="home">
    <UseExternalAPI msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import UseExternalAPI from "@/components/UseExternalAPI.vue";

export default {
  name: "Home",
  components: {
    UseExternalAPI,
  },
};
</script>
