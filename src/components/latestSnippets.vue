<template>
  <div>
    <div class="latest-btn-container">
      <button class="show-latest-button" @click="getLatestSnippets">Show latest</button>
    </div>
    <div v-if="model">
      <div class="latest-container" v-for="item in model" :key="item.id">
        <div class="latest-body">
          <p class="latest-title">Title: {{item.title}}</p>
          <p>Content: {{item.content}}</p>
          <p class="item-id">ID: {{item.id}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const baseUrl = "https://www.forverkliga.se/JavaScript/api/api-snippets.php";

export default {
  data: () => ({
    model: null
  }),
  methods: {
    async getLatestSnippets() {
      try {
        let response = await this.$http.get(baseUrl, {
          params: { latest: "" }
        });

        this.model = response.data;
        console.log(response.data);
      } catch (error) {
        console.log("Something went wrong", error);
      }
    }
  }
};
</script>

<style scoped>
.latest-btn-container {
  display: flex;
  justify-content: center;
}
.show-latest-button {
  width: 30em;
  height: 3em;
  margin-bottom: 1em;
  text-transform: uppercase;
  font-weight: 700;
  background-color: #619edb;
  border: 1px solid black;
  cursor: pointer;
}
.show-latest-button:hover {
  background-color: #548bc2;
}
.latest-container {
  display: flex;
  justify-content: center;
}
.latest-body {
  position: relative;
  margin: 1.3em;
  padding-left: 1.2em;
  background-color: white;
  border: 2px solid rgba(0, 0, 0, 0.8);
  width: 40vw;
  height: 8em;
}
.latest-title {
  margin-top: -20px;
  font-weight: 700;
}
.item-id {
  position: absolute;
  margin-right: 1em;
  right: 0;
  bottom: 0;
}
</style>;
