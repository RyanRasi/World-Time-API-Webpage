<template>
  <div class="area-and-locations">
    <div class="container">
      <div class="area">
        <select class="form-control" v-model="selectedArea" @click="areaClicked()">
          <option>Choose Area</option>
          <option
            v-bind:key="timezone"
            v-for="timezone in timezone"
            v-bind:value="timezone"
          >{{ timezone }}</option>
        </select>
      </div>
      <div class="location">
        <select class="form-control" v-model="selectedLocation" @click="locationClicked()">
          <option>Choose Location</option>
          <option
            v-bind:key="locations"
            v-for="locations in locations"
            v-bind:value="locations"
          >{{ locations }}</option>
        </select>
      </div>
    </div>
    <div class="time">
      <h4>{{time}}</h4>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "AreaAndLocations",
  components: {},
  data() {
    return {
      selectedLocation: "Choose Location",
      locations: [],
      time: "",
      selectedArea: "Choose Area",
      timezone: [
        "Africa",
        "America",
        "Antarctica",
        "Asia",
        "Atlantic",
        "Australia",
        "Europe",
        "Indian",
        "Pacific"
      ]
    };
  },
  methods: {
    areaClicked() {
      this.selectedLocation = "Choose Location";
      this.time = "";
      if (this.selectedArea === "Choose Area") {
        this.locations = [];
        this.selectedLocation = "Choose Location";
      } else {
        axios
          .get("http://worldtimeapi.org/api/timezone/" + this.selectedArea)
          .then(res => (this.locations = res.data))
          .catch(error => console.log(error));
      }
    },
    locationClicked() {
      if (this.selectedLocation !== "Choose Location") {
        axios
          .get("http://worldtimeapi.org/api/timezone/" + this.selectedLocation)
          .then(
            res =>
              (this.time =
                "The time is: " +
                res.data.datetime.substring(
                  res.data.datetime.lastIndexOf("T") + 1,
                  res.data.datetime.lastIndexOf(".")
                ))
          )
          .catch(error => console.log(error));
      }
    }
  }
};
</script>
<style lang="css" scoped>
.container {
  column-count: 1;
  text-align: center;
}
.time {
  font-size: 40px;
}
select {
  font-size: 20px;
}
</style>