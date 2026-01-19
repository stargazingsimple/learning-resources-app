<script>
import ResourceListItem from "@/components/Resource/ResourceListItem.vue";

export default {
  name: "ResourceList",
  components: { ResourceListItem },
  inject: ["resources"],
};
</script>

<template>
  <ul>
    <resource-list-item
      v-for="resource in resources"
      v-bind="resource"
      :key="resource.id"
    />
  </ul>
</template>

<style scoped>
ul {
  list-style: none;
  margin: 0 auto;
  padding: 0;
  max-width: 40rem;
}
</style>
