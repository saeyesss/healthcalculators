<template>
  <div>
    <v-dialog max-width="400">
      <template v-slot:activator="{ on }">
        <v-btn
          slot="activator"
          outlined
          color="blue lighten-3"
          dark
          v-on="on"
          small
          >Update</v-btn
        >
      </template>
      <v-flex>
        <v-card
          height="100%"
          max-width="400"
          elevation="4"
          dark
          color="#0C6FF9"
          class="mx-auto"
        >
          <v-card-title>
            <span class="font-size-heavy display-1">
              BMR Calculator
            </span></v-card-title
          >

          <v-main class="container">
            <div>
              <div>
                <v-radio-group v-model="gender" row>
                  <v-radio
                    clearable
                    filled
                    dense
                    label="Male"
                    class="ml-4"
                    value="male"
                  />
                  <v-radio
                    clearable
                    filled
                    dense
                    label="Female"
                    class=""
                    value="female"
                  />
                </v-radio-group>
                <v-text-field
                  v-model="age"
                  filled
                  dense
                  clearable
                  label="Age"
                  class="px-2"
                />

                <v-text-field
                  v-model="weight"
                  filled
                  dense
                  clearable
                  label="Weight (kg)"
                  class="px-2"
                />

                <v-text-field
                  v-model="height"
                  clearable
                  filled
                  dense
                  label="Height (cm)"
                  class="px-2"
                />
              </div>
              <div pa-4>
                <v-btn class="ml-15" light @submit="calculatebmr"
                  ><v-icon left>mdi-calculator</v-icon> Calculate
                </v-btn>

                <v-btn class="ml-4" light @click="save"
                  ><v-icon left>mdi-content-save</v-icon> Save
                </v-btn>
              </div>
            </div>
            <v-banner sticky class="result">
              <span class="font-size-heavy title">
                Basal Metabolic Rate: {{ result }}
              </span>
            </v-banner>
          </v-main>
        </v-card>
      </v-flex>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      gender: "",
      age: "",
      weight: "",
      height: "",
      result: "",
    };
  },

  // CALCULATEBMR NOT WORKING PLEASE FIX
  methods: {
    calculatebmr() {
      // let gender = this.gender;
      // let height = parseFloat(this.height);
      // let weight = parseFloat(this.weight);
      // let age = parseFloat(this.age);
      // if (gender == "male") {
      //   this.result = parseFloat(
      //     370 +
      //       21.6(
      //         1 -
      //           parseFloat(
      //             1.2 * parseFloat(weight / (height * height)) +
      //               0.23 * age -
      //               16.2
      //           )
      //       ) *
      //         weight
      //   );
      // } else if (gender == "female") {
      //   this.result = parseFloat(
      //     370 +
      //       21.6(
      //         1 -
      //           parseFloat(
      //             1.2 * parseFloat(weight / (height * height)) +
      //               0.23 * age -
      //               5.4
      //           )
      //       ) *
      //         weight
      //   );
      // }
      // let result = parseFloat("40392");
    },
  },
};
</script>

<style></style>
