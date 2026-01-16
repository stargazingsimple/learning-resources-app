<script>
import ResourceListItem from "@/components/Resources/ResourceListItem.vue";

export default {
  name: "ResourceList",
  components: { ResourceListItem },
  props: {
    resources: {
      type: Array,
      required: true,
    },
  },
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
