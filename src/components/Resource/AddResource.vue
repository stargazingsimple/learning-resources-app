<script>
import BaseCard from "@/components/UI/BaseCard.vue";
import BaseButton from "@/components/UI/BaseButton.vue";
import BaseDialog from "@/components/UI/BaseDialog.vue";

export default {
  name: "AddResource",
  components: { BaseButton, BaseCard, BaseDialog },
  inject: ["addResource"],
  data() {
    return {
      resource: {
        title: "",
        description: "",
        link: "",
      },
      isValidForm: true,
    };
  },
  methods: {
    submit() {
      if (
        !this.resource.title.trim() ||
        !this.resource.description.trim() ||
        !this.resource.link.trim()
      ) {
        this.isValidForm = false;
        return;
      }
      this.addResource({
        id: Math.random().toString(),
        ...this.resource,
      });
      this.resetForm();
    },
    resetForm() {
      this.resource.title = "";
      this.resource.description = "";
      this.resource.link = "";
    },
    closeDialog() {
      this.isValidForm = true;
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
  <base-dialog
    :open="!isValidForm"
    :title="'Invalid values'"
    @close-dialog="closeDialog"
  >
    <template #content>
      <p>Unfortunately, at least one input value is invalid</p>
      <p>
        Please check all inputs and make sure you enter at least a few
        characters into each input field
      </p>
    </template>
    <template #actions>
      <base-button @click="closeDialog">Close</base-button>
    </template>
  </base-dialog>
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
