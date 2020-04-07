<template>
  <div>
    <sharingForm></sharingForm>
    <removeSnippet></removeSnippet>
    <latestSnippets></latestSnippets>
  </div>
</template>

<script>
import sharingForm from "./components/sharingForm.vue";
import latestSnippets from "./components/latestSnippets.vue";
import removeSnippet from "./components/removeSnippet.vue";

export default {
  name: "App",
  components: {
    sharingForm,
    latestSnippets,
    removeSnippet
  }
};
</script>

<style>
body {
  background-color: #7b8a8f;
}
</style>
