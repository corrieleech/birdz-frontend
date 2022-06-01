<script>
import "axios";
import Datepicker from "@vuepic/vue-datepicker";
import "@vuepic/vue-datepicker/dist/main.css";
import { ref } from "vue";
import axios from "axios";

export default {
  components: {
    Datepicker,
  },
  setup() {
    const userTimeEntry = ref(new Date());

    return {
      userTimeEntry,
    };
  },
  data: function () {
    return {
      message: "Bird New List!",
      birder: localStorage.getItem("birder"),
      checklistName: "",
      location: "L161180",
    };
  },
  created: function () {},
  methods: {
    createList() {
      console.log("List created!");
      axios({
        method: "post",
        url: "/checklists/",
        data: {
          name: this.checklistName,
          locId: this.location,
          time: this.userTimeEntry,
        },
      }).then(function (response) {
        console.log("success!!", response.data);
      });
    },
  },
};
</script>

<template>
  <div class="checklist-new">
    <div>
      <h2>Name Your Checklist</h2>
      <input v-model="checklistName" />
      <h2>Enter Day And Time for Checklist</h2>
      <Datepicker v-model="userTimeEntry" placeholder="Select Day and Time" :is24="false" />
      {{ userTimeEntry }}
    </div>
    <button v-on:click="createList()">Create your list</button>
  </div>
</template>

<style></style>
