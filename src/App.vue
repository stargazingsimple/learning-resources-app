<script>
import ResourceItem from "@/components/Resources/ResourceItem.vue";

export default {
  name: "App",
  components: { ResourceItem },
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
  <resource-item
    v-for="resource in resources"
    v-bind="resource"
    :key="resource.id"
  />
</template>
