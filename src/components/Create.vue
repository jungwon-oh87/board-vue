<template>
  <div>
    <input v-model="author" placeholder="author" type="text" />
    <input v-model="title" placeholder="title" type="text" />
    <textarea v-model="content" placeholder="content" />
    <button @click="submit">submit</button>
  </div>
</template>

<script>
import data from "../data/";

export default {
  name: "Create",
  data() {
    return {
      data: data,
      author: "",
      title: "",
      content: "",
    };
  },
  methods: {
    submit() {
      this.data.push({
        author: this.author,
        title: this.title,
        content: this.content,
      });
      this.$router.push({
        path: "/",
      });
    },
  },
};
</script>

<style>
</style>