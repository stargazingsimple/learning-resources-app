<script>
import BaseCard from "@/components/UI/BaseCard.vue";
import BaseButton from "@/components/UI/BaseButton.vue";
import ResourceList from "@/components/Resource/ResourceList.vue";
import AddResource from "@/components/Resource/AddResource.vue";

export default {
  name: "ResourceTabs",
  components: { BaseButton, BaseCard, ResourceList, AddResource },
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
      selectedTab: "resource-list",
      tabs: [
        {
          title: "Resource List",
          name: "resource-list",
        },
        {
          title: "Add Resource",
          name: "add-resource",
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.resources,
      addResource: this.addResource,
    };
  },
  methods: {
    setSelectedTab(name) {
      this.selectedTab = name;
    },
    addResource(resource) {
      this.resources.push(resource);
      this.selectedTab = "resource-list";
    },
  },
};
</script>

<template>
  <base-card>
    <base-button
      v-for="{ title, name } in tabs"
      :key="title"
      :is-flat="selectedTab !== name"
      @click="setSelectedTab(name)"
    >
      {{ title }}
    </base-button>
  </base-card>
  <keep-alive>
    <component :is="selectedTab" />
  </keep-alive>
</template>
