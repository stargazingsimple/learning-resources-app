<script>
import ResourceListItem from "@/components/Resource/ResourceListItem.vue";
import BaseCard from "@/components/UI/BaseCard.vue";

export default {
  name: "ResourceList",
  components: { BaseCard, ResourceListItem },
  inject: ["resources"],
};
</script>

<template>
  <ul v-if="resources.length">
    <resource-list-item
      v-for="resource in resources"
      v-bind="resource"
      :key="resource.id"
    />
  </ul>
  <base-card v-else>
    <h2>Empty data</h2>
  </base-card>
</template>

<style scoped>
ul {
  list-style: none;
  margin: 0 auto;
  padding: 0;
  max-width: 40rem;
}

h2 {
  text-align: center;
}
</style>
