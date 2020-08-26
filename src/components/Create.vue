<template>
  <div>
    <b-input v-model="author" placeholder="author" type="text" />
    <b-input v-model="title" placeholder="title" type="text" />
    <b-textarea v-model="content" placeholder="content" />
    <b-button @click="index !== undefined ? update() : write()">{{
      index !== undefined ? "update" : "submit"
    }}</b-button>
    <b-button @click="cancel">Cancel</b-button>
  </div>
</template>

<script>
import data from "../data/";

export default {
  name: "Create",
  data() {
    const index = this.$route.params.contentId;
    return {
      data: data,
      index: index,
      author: index !== undefined ? data[index].author : "",
      title: index !== undefined ? data[index].title : "",
      content: index !== undefined ? data[index].content : ""
    };
  },
  methods: {
    write() {
      console.log("write called");
      this.data.push({
        author: this.author,
        title: this.title,
        content: this.content
      });
      this.$router.push({
        path: "/"
      });
    },
    update() {
      data[this.index].author = this.author;
      data[this.index].title = this.title;
      data[this.index].content = this.content;
      this.$router.push({
        path: "/"
      });
    },
    cancel() {
      this.$router.push({
        path: "/"
      });
    }
  }
};
</script>

<style></style>
