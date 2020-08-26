<template>
  <div>
    <b-table
      striped
      hover
      :items="data"
      @row-clicked="getDetail"
      :fields="fields"
    ></b-table>
    <b-button v-on:click="write">Write Something</b-button>
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
      fields: [
        { key: "author", label: "저자" },
        { key: "title", label: "제목" },
        { key: "content", label: "내용" }
      ],
      data: data
    };
  }
};
</script>

<style></style>
