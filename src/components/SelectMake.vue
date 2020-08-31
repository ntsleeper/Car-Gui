


<template>

    <v-col class="d-flex" cols="12" sm="6">
        <v-select
          :items="items"
          filled
          label="Filled style"
          dense
        ></v-select>
    </v-col>


</template>


<script>

export default {
    el: '#selectmake',
    name: 'SelectMake'
    

    data: () => ({
    
    all_makes: getAllMakes(),

    test: false,
  }),

    methods: {
    requestCarInformation: function() {
      alert("hello");
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
        return result;
    },
  },

}

</script>

<style scoped>





</style>