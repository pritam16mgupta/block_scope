<template>
  <div>
    <v-container>
      <v-row class="float-right">
        <v-alert
          v-model="alert"
          dismissible
          color="orange"
          border="left"
          elevation="2"
          colored-border
          icon="mdi-coin-outline"
          transition="slide-x-transition"
        >
          You've transfered
          <strong>{{coin}}</strong>
          to doctor {{selectedDoctor}}!.
        </v-alert>
      </v-row>
      <v-row>
        <v-col cols="12" sm="4">
          <p>Doctors</p>

          <v-overflow-btn
            class="my-2"
            :items="dropdown_edit"
            label="Doctors"
            editable
            item-value="text"
            @change="latestData"
          ></v-overflow-btn>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="4">
          Your Current Balance :
          <v-chip class="ma-2" color="orange" text-color="white">
            <v-icon left>mdi-coin-outline</v-icon>
            {{currentcoin}}
          </v-chip>
        </v-col>
        <v-col cols="8">
          <v-text-field
            v-model="coin"
            outlined
            clearable
            label="Transfer Money to Doctors"
            type="text"
          ></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12">
          <v-textarea label="History" auto-grow outlined rows="1" row-height="15"></v-textarea>
        </v-col>
      </v-row>
      <!-- <template>
        <v-row align="center">
          <v-expansion-panels :focusable="true">
            <v-expansion-panel v-for="(item,i) in 5" :key="i">
              <v-expansion-panel-header>Item</v-expansion-panel-header>
              <v-expansion-panel-content>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</v-expansion-panel-content>
            </v-expansion-panel>
          </v-expansion-panels>
        </v-row>
      </template> -->
      <v-row class="float-right">
        <v-btn :loading="btnloading" color="blue-grey" class="ma-2 white--text" @click="submit">Save</v-btn>
      </v-row>
    </v-container>
  </div>
</template>
    </v-container>
  </div>
</template>
<script>
export default {
  data: () => ({
    dropdown_edit: [
      { text: "10Doctor1" },
      { text: "7Doctor1" },
      { text: "5Doctor1" },
      { text: "2Doctor1" },
      { text: "Doctor1" }
    ],
    currentcoin: 200,
    alert: false,
    coin: 0,
    selectedDoctor: null,
    btnloading: false
  }),
  methods: {
    submit() {
      if (this.coin > 0) {
        this.currentcoin = this.currentcoin - parseInt(this.coin);
        this.alert = true;
        setTimeout(() => {
          this.alert = false;
        }, 3000);
      } else {
        alert("Coin must be greater then 0");
      }
    },
    latestData(doctor) {
      this.selectedDoctor = doctor;
    }
  }
};
</script>