<template>
  <div>
    <div class="remove-container">
      <input type="text" v-model="snippetId" placeholder="Enter id" />
      <button @click="removeSnippet">Remove snippet by id</button>
    </div>
    <p v-show="success">Removed snippet</p>
  </div>
</template>

<script>
const baseUrl = "https://www.forverkliga.se/JavaScript/api/api-snippets.php";

export default {
  data: () => ({
    snippetId: "",
    success: false
  }),
  methods: {
    async removeSnippet() {
      try {
        let response = await this.$http.post(baseUrl, {
          delete: "",
          id: this.snippetId
        });
        this.snippetId = "";
        if (response.data.status == "success") {
          this.success = true;
        }
        console.log(response.data);
      } catch (error) {
        console.log("Something went wrong", error);
      }
    }
  }
};
</script>



<style scoped>
.remove-container {
  margin: 1em;
  display: flex;
  justify-content: center;
  align-items: center;
}
input {
  width: 14em;
}
button {
  width: 14em;
  margin-left: 1em;
}
p {
  text-align: center;
  color: rgb(17, 187, 17);
}
</style>