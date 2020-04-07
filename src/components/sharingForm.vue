<template>
  <div class="main-content">
    <h1>Welcome to code share!</h1>
    <div class="form-center">
      <div class="form-area">
        <p>Enter a title:</p>
        <input v-model="title" type="text" />
        <p>Enter code:</p>
        <textarea v-model="content" cols="30" rows="10"></textarea>
        <button @click="uploadSnippet">Add snippet</button>
        <p class="addedSnippet" v-if="success">Added snippet!</p>
      </div>
    </div>
  </div>
</template>

<script>
const baseUrl = "https://www.forverkliga.se/JavaScript/api/api-snippets.php";

export default {
  data: () => ({
    title: "",
    content: "",
    success: false
  }),
  methods: {
    async uploadSnippet() {
      try {
        let response = await this.$http.post(baseUrl, {
          add: "",
          title: this.title,
          content: this.content
        });
        this.title = "";
        this.content = "";
        if (response.data.status == "success") {
          this.success = true;
        }
      } catch (error) {
        console.log("Something went wrong", error);
      }
    }
  }
};
</script>
 
<style scoped>
p {
  margin: 0;
  margin-top: 1em;
}
h1 {
  display: flex;
  justify-content: center;
}
.form-area {
  display: flex;
  flex-direction: column;
}
input {
  width: inherit;
}
textarea {
  width: 30em;
}
.form-center {
  display: flex;
  justify-content: center;
}
.addedSnippet {
  text-align: center;
  color: rgb(53, 153, 53);
}
</style>
