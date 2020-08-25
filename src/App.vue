<template>
  <v-app id="inspire">
    <v-app-bar app color="indigo" dark>
      <v-toolbar-title>Car-Gui</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <template>
        <v-container class="grey lighten-5">
          <v-row no-gutters>
            <v-col cols="6" md="4">
              <v-card class="pa-2" outlined tile>
                <v-combobox
                  v-model="select"
                  :items="items"
                  label="Car Makes"
                  multiple
                ></v-combobox>
                <v-btn
                  v-on:click="requestCarInformation()"
                  small
                  color="primary"
                  >Search</v-btn
                >
              </v-card>
            </v-col>
            <v-col cols="12" sm="6" md="8">
              <v-card class="pa-2" outlined tile>
                <template>
                  <v-data-table
                    :headers="car_table"
                    :items="desserts"
                    :items-per-page="5"
                    class="elevation-1"
                  ></v-data-table>
                </template>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </template>
    </v-main>

    <v-footer color="indigo" app>
      <span class="white--text"
        >&copy; {{ new Date().getFullYear() }} Spencer Thomas</span
      >
    </v-footer>
  </v-app>
</template>

<script>
export default {
  props: {
    source: String,
  },
  data: () => ({
    car_table: [
      { text: "Makes", value: "Makes" },
      { text: "Models", value: "Models" },
      { text: "Value", value: "value" },
    ],
    test: false,
  }),

  methods: {
    requestCarInformation: function() {
      alert("hello");
    },
  },
};
</script>
