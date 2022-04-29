<template>
  <v-container
    fluid
    class="py-50 px-50"
    bg
    fill-height
    grid-list-md
    color="purple"
  >
    <v-layout row wrap align-center>
      <v-flex>
        <v-card hover class="pa-0 ma-5" style="height: 100%">
          <v-row class="text-center pa-0 ma-0">
            <v-col
              cols="12"
              md="6"
              lg="5"
              class="pa-5 ma-0 text-left"
              style="height: 500px"
            >
              <h2 class="text-left">{{ datas.title }}</h2>
              <v-sheet
                color="#F3E5F5"
                elevation="6"
                class="pt-2 pb-2 mt-8 mb-5 text-center"
                outlined
                rounded
                shaped
                width="250"
                style="color: #7c007c"
                >{{ datas.begin_at | formatDate }} -
                {{ datas.end_at | formatDate }}</v-sheet
              >
              <p class="text-justify pt-5 pb-5">
                Morbi mattis ullamcorper velit. Donec orci lectus, aliquam ut,
                faucibus non, euismod id, nulla. Fusce convallis metus id felis
                luctus adipiscing. Aenean massa. Vestibulum purus quam,
              </p>
              <v-content class="mt-5 mb-5">
                <v-icon large color="teal darken-2"> mdi-email </v-icon>
                <span> {{ datas._embedded.address.address }}</span>
              </v-content>

              <v-content v-if="datas.is_webinar" class="mt-5 mb-5">
                <v-icon large color="blue-grey darken-2">
                  mdi-call-split
                </v-icon>
                <span> webinarUrl</span>
              </v-content>

              <v-btn
                color="purple"
                :href="datas.web_url"
                elevation="2"
                style="color: white"
                >En savoir plus</v-btn
              >
            </v-col>
            <v-col cols="12" md="6" lg="7" class="pa-0 ma-0">
              <v-card
                class="pa-5 ma-0"
                color="blue"
                v-bind:img="datas.cover"
                style="height: 500px; background-size: cover"
              >
              </v-card>
            </v-col>
          </v-row>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      datas: [],
    };
  },
  mounted() {
    axios.get("http://localhost:8080/api.json").then((response) => {
      this.datas = response.data;
    });
  },
};
</script>