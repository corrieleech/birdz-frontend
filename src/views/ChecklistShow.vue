<script>
import axios from "axios";
import ChecklistBird from "../components/ChecklistBird.vue";

export default {
  components: { ChecklistBird },
  data: function () {
    return {
      message: "Bird Checklist!",
      birder: localStorage.getItem("birder"),
      likelyBirds: [],
      checklist: {},
    };
  },
  created: function () {
    axios.get(`/checklists/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.checklist = response.data;
      this.likelyBirds = response.data.likely_birds;
    });
  },
  methods: {
    updateLikelyBird: function (likelyBirdId) {
      axios.patch(`/likely-birds/${likelyBirdId}`).then((response) => {
        console.log("Successfully updated!", response.data);
      });
    },
  },
};
</script>

<template>
  <div class="checklist-show">
    <h1>{{ checklist.name }}</h1>
    <h2>{{ checklist.simple_date }}</h2>
    <ChecklistBird v-for="bird in likelyBirds" v-bind:key="bird.id">
      <input
        type="checkbox"
        v-model="bird.has_seen"
        id="likely-bird"
        class="bigCheckbox"
        v-on:click="updateLikelyBird(bird.id)"
      />
      {{ bird.bird_name }}
    </ChecklistBird>
  </div>
</template>

<style></style>
