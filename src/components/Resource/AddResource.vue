<script>
import BaseCard from "@/components/UI/BaseCard.vue";
import BaseButton from "@/components/UI/BaseButton.vue";

export default {
  name: "AddResource",
  components: { BaseButton, BaseCard },
  inject: ["addResource"],
  data() {
    return {
      resource: {
        title: "",
        description: "",
        link: "",
      },
    };
  },
  methods: {
    submit() {
      if (
        !this.resource.title.trim().length ||
        !this.resource.description.trim().length ||
        !this.resource.link.trim().length
      ) {
        alert("Invalid values");
        return;
      }
      this.addResource({
        id: Math.random(),
        ...this.resource,
      });
      this.resetForm();
    },
    resetForm() {
      this.resource.title = "";
      this.resource.description = "";
      this.resource.link = "";
    },
  },
};
</script>

<template>
  <base-card>
    <form @submit.prevent="submit">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" id="title" v-model="resource.title" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea id="description" rows="3" v-model="resource.description" />
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" id="link" v-model="resource.link" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
