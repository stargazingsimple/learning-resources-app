<script>
import TheHeader from "@/components/Layouts/TheHeader.vue";
import ResourceTabs from "@/components/Resource/ResourceTabs.vue";

export default {
  name: "App",
  components: { ResourceTabs, TheHeader },
};
</script>

<template>
  <the-header title="Learning Resources" />
  <resource-tabs />
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
}
</style>
