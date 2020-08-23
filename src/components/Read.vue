<template>
  <div>
    <b-table striped hover :items="data" @row-clicked="getDetail"></b-table>
    <!-- <tr :key="index" v-for="(d,index) in data" @click="getDetail(index)">
        <td>{{d.author}}</td>
        <td>{{d.title}}</td>
        <td>{{d.content}}</td>
    </tr> -->
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
        path: "Create"
      });
    },
    getDetail(row, index) {
      //   console.log("row clicked!", row);
      //   console.log("row clicked!", index);
      this.$router.push({
        name: "Detail",
        params: {
          contentId: index
        }
      });
    }
  },
  data() {
    return {
      data: data
    };
  }
};
</script>

<style></style>
