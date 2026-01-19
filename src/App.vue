<script>
import ResourceList from "@/components/Resources/ResourceList.vue";
import TheHeader from "@/components/Layouts/TheHeader.vue";

export default {
  name: "App",
  components: { ResourceList, TheHeader },
  data() {
    return {
      resources: [
        {
          id: Math.random().toString(),
          title: "Google",
          description: "Google platform",
          link: "https://google.com",
        },
        {
          id: Math.random().toString(),
          title: "Udemy",
          description: "Udemy platform",
          link: "https://udemy.com",
        },
        {
          id: Math.random().toString(),
          title: "Vue",
          description: "Vue js platform",
          link: "https://vuejs.org",
        },
      ],
    };
  },
};
</script>

<template>
  <the-header title="Learning Resources" />
  <resource-list :resources="resources" />
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
