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
                <v-col class="d-flex" cols="12" sm="6">
                  <v-select
                    v-model="make_result"
                    :items="all_makes"
                    item-text="make"
                    label="Choose a make"
                    result="value;"
                  ></v-select>
                </v-col>
                <div v-if="all_makes">
                  <p>{{ make_result }}</p>
                </div>
              </v-card>
            </v-col>
            <v-col cols="12" sm="6" md="8">
              <v-btn small v-on:click="testCommunicate()">Normal</v-btn>
              <v-card class="pa-2" outlined tile>
                <template>
                  <v-data-table
                    :headers="car_table"
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
// import SelectMake from './components/SelectMake';

export default {
  name: "app",
  components: {
    // SelectMake
  },

  created: function() {
    this.getAllMakes();
  },

  props: {
    source: String,
  },
  data: () => ({
    all_makes: "",
    make_result: "",

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

    async testCommunicate() {
      var bodyFormData = new FormData();
      bodyFormData.append("request_id", "hello from js to php");

      this.$http({
        method: "POST",
        url: "http://localhost/carPHP/src/getMakes.php",
        data: bodyFormData,
        headers: {
          "Content-Type": "multipart/form-data",
        },
      })
        .then(function(response) {
          console.log(response);
        })
        .catch(function(response) {
          console.log(response);
        });
    },
    async getAllMakes() {
      let config = {
        headers: {
          Accept: "application/json",
        },
      };
      var result = await this.$http.get(
        "http://localhost/carPHP/src/getMakes.php",
        config
      );
      alert(result.statusText);
      this.all_makes = result.data;
    },
  },
};
</script>
