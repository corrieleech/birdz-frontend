<script>
export default {
  data: function () {
    return {
      message: "Bird New List!",
      birder: localStorage.getItem("birder"),
      likelyBirds: [],
      checklist: {},
    };
  },
  created: function () {},
  methods: {},
};
</script>

<template>
  <div class="checklist-new">
    {{ message }}
  </div>
</template>

<style></style>
