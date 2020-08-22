<template>
  <div>
    <table>
      <tr>
        <td>Author</td>
        <td>Title</td>
        <td>Content</td>
      </tr>
      <tr :key="index" v-for="(d,index) in data" @click="getDetail(index)">
        <td>{{d.author}}</td>
        <td>{{d.title}}</td>
        <td>{{d.content}}</td>
      </tr>
    </table>
    <button v-on:click="write">Write Something</button>
  </div>
</template>

<script>
import data from "@/data";
export default {
  name: "Read",
  methods: {
    write() {
      // console.log("write called");
      this.$router.push({
        path: "Create",
      });
    },
    getDetail(index) {
      this.$router.push({
        name: "Detail",
        params: {
          contentId: index,
        },
      });
    },
  },
  data() {
    return {
      data: data,
    };
  },
};
</script>

<style>
</style>