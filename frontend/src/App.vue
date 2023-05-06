<script>
import AppHeader from "@/components/AppHeader.vue";

export default {
  components: {
    AppHeader,
  },
};
</script>

<template>
  <div id="app">
    <!-- <AppHeader /> -->

    <div class="container">
      <router-view />
    </div>
  </div>
</template>

<style>
body {
  background-color: rgba(0, 213, 255, 0.2) !important;
}

.page {
  max-width: 400px;
  margin: auto;
}

.login_page,
.register_page {
  max-width: 400px;
  margin: 0 auto;
}
</style>
