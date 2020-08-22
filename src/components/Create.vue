<template>
  <div>
    <input v-model="author" placeholder="author" type="text" />
    <input v-model="title" placeholder="title" type="text" />
    <textarea v-model="content" placeholder="content" />
    <button
      @click="index !== undefined ? update() : write()"
    >{{index !== undefined ? "update" : "submit"}}</button>
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
      content: index !== undefined ? data[index].content : "",
    };
  },
  methods: {
    write() {
      console.log("write called");
      this.data.push({
        author: this.author,
        title: this.title,
        content: this.content,
      });
      this.$router.push({
        path: "/",
      });
    },
    update() {
      data[this.index].author = this.author;
      data[this.index].title = this.title;
      data[this.index].content = this.content;
      this.$router.push({
        path: "/",
      });
    },
  },
};
</script>

<style>
</style>