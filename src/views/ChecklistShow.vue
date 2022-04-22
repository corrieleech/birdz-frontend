<script>
import axios from "axios";
import CardItem from "@/components/CardItem.vue";

export default {
  data: function () {
    return {
      message: "Hello View",
      checklist: [],
    };
  },
  components: { CardItem },
  created: function () {
    axios.get(`/checklists/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.checklist = response.data;
    });
  },
  methods: {},
};
</script>

<template>
  <div class="checklist-show">
    <h1>{{ message }}</h1>
    {{ checklist.likely_birds }}
    <card-item v-for="bird in checklist.likely_birds" v-bind:key="bird.id">
      {{ bird.name }}
    </card-item>
  </div>
</template>

<style></style>
