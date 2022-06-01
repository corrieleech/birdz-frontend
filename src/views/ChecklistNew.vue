<script>
import "axios";
import Datepicker from "@vuepic/vue-datepicker";
import "@vuepic/vue-datepicker/dist/main.css";
// import { ref } from "vue";

export default {
  components: {
    Datepicker,
  },
  data: function () {
    return {
      message: "Bird New List!",
      birder: localStorage.getItem("birder"),
      likelyBirds: [],
      checklist: {},
      picked: {},
      time: {
        year: "",
        month: "",
        day: "",
        hour: "",
        minute: "",
      },
    };
  },
  created: function () {},
  methods: {
    createList() {
      console.log("List created!");
      console.log(this.picked);
    },
  },
};
</script>

<template>
  <div class="checklist-new">
    <div>
      <h2>Enter time</h2>
      <datepicker v-model="picked" />
      {{ picked }}
    </div>
    <button v-on:click="createList()">Create your list</button>
  </div>
</template>

<style></style>
