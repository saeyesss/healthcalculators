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
          elevation="6"
          dark
          color="#0C6FF9"
          class="mx-auto"
        >
          <v-card-title>
            <span class="font-size-heavy display-1">
              BMI Calculator
            </span></v-card-title
          >

          <v-main class="container">
            <div>
              <div>
                <v-text-field
                  v-model="weight"
                  filled
                  dense
                  clearable
                  label="Weight (kg)"
                  class="px-5"
                />

                <v-text-field
                  v-model="height"
                  clearable
                  filled
                  dense
                  label="Height (cm)"
                  class="px-5"
                />
              </div>
              <div pa-4>
                <v-btn class="white ml-15" light @click="calculatebmi"
                  ><v-icon left>mdi-calculator</v-icon> Calculate
                </v-btn>

                <v-btn class="ml-4" light @click="saveBMI"
                  ><v-icon left>mdi-content-save</v-icon> Save
                </v-btn>
              </div>
            </div>
            <v-banner sticky class="result">
              <span class="font-size-heavy title">BMI: {{ result }}</span>
            </v-banner>
          </v-main>
        </v-card>
      </v-flex>
    </v-dialog>
  </div>
</template>

<script>
import { db } from "../main";
// import firestore from "firebase/firestore";
export default {
  data() {
    return {
      weight: "",
      height: "",
      result: "",
      usersBMI: [],
      newUserBMI: "",
    };
  },

  firestore() {
    return {
      usersBMI: db.collection("usersBMI"),
    };
  },

  methods: {
    calculatebmi() {
      let weight = parseFloat(this.weight);
      let height = parseFloat(this.height) / 100;
      this.result = parseFloat(weight / (height * height)).toFixed(2);
    },
    saveBMI() {
      let newUserBMI = this.result;
      this.$firestore.users.add({
        bmi: newUserBMI,
        timestamp: new Date(),
      });
      this.newUserBMI = "";
    },
  },

  //       String uid = FirebaseAuth.getInstance().getCurrentUser().getUid();
  // FirebaseFirestore rootRef = FirebaseFirestore.getInstance();
  // DocumentReference uidRef = rootRef.collection("users").document(uid);

  // async saveBMI() {
  //         let ref = await db.collection("users");
  //         ref.where("user_id", "==", firebase.auth().currentUser.uid).add({
  //             newInput: this.newInput
  //         });
};
</script>

<style></style>
