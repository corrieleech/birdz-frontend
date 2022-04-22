<script>
import { ref } from "vue";
import AirportCards from "@/components/AirportCards.vue";
import usAirportData from "/data/us-airports.js";
import euAirportData from "/data/eu-airports.js";
import CardItem from "@/components/CardItem.vue";

export default {
  components: { AirportCards, CardItem },
  setup() {
    const usAirports = ref(usAirportData);
    const euAirports = ref(euAirportData);
    return { usAirports, euAirports };
  },
};
</script>

<template>
  <airport-cards :airports="usAirports" />
  <airport-cards :airports="euAirports" />
  <card-item>
    <p>US Airports</p>
    <p>Total: {{ usAirports.length }}</p>
  </card-item>
  <card-item>
    <p>Eu Airports</p>
    <p>Total: {{ euAirports.length }}</p>
  </card-item>
</template>

<style>
.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 1rem;
  max-width: 960px;
  margin: 0 auto;
}

.card {
  border: 3px solid;
  border-radius: 0.5rem;
  padding: 1rem;
  margin-bottom: 1rem;
}

.card p:first-child {
  font-weight: bold;
  font-size: 2.5rem;
  margin: 1rem 0;
}

.card p:last-child {
  font-style: italic;
  font-size: 0.8rem;
}
</style>
