<template>
  <div>
    <v-form>
      <v-container>
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
          You've added
          <strong>{{coin}}</strong> to your wallet!.
        </v-alert>
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
              label="Add Money To Your Wallet"
              type="text"
            >
              <template v-slot:append>
                <v-fade-transition leave-absolute>
                  <v-btn class="mt-n2" fab dark small color="primary" @click="addMoney">
                    <v-icon dark>mdi-plus</v-icon>
                    <v-tooltip>Add Money To Your Wallet</v-tooltip>
                  </v-btn>
                </v-fade-transition>
              </template>
            </v-text-field>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
    <v-container>
    <v-card>
      <v-card-title>
        Wallet
        <div class="flex-grow-1"></div>
        <v-text-field
          v-model="search"
          append-icon="mdi-search"
          label="Search"
          single-line
          hide-details
        ></v-text-field>
      </v-card-title>
      <v-data-table :headers="headers" :items="desserts" :search="search">
        <template v-slot:item.direction="{ item }">
          <v-icon :color="getColor(item.direction)">mdi-arrow-{{item.direction}}-thick</v-icon>
        </template>
      </v-data-table>
    </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentcoin: 200,
      coin: 0,
      alert: false,
      search: "",
      headers: [
        {
          text: "To",
          align: "left",
          value: "to"
        },
        { text: "Direction", value: "direction", sortable: false },
        { text: "From", value: "from" },
        { text: "Amount in ($)", value: "amount" }
      ],
      desserts: [
        {
          to: "Frozen Yogurt",
          direction: "left",
          from: 6.0,
          amount: 24,
          protein: 4.0,
          iron: "1%"
        },
        {
          to: "Ice cream sandwich",
          direction: "right",
          from: 9.0,
          amount: 37,
          protein: 4.3,
          iron: "1%"
        },
        {
          to: "Eclair",
          direction: "left",
          from: 16.0,
          amount: 23,
          protein: 6.0,
          iron: "7%"
        },
        {
          to: "Cupcake",
          direction: "left",
          from: 3.7,
          amount: 67,
          protein: 4.3,
          iron: "8%"
        },
        {
          to: "Gingerbread",
          direction: "left",
          from: 16.0,
          amount: 49,
          protein: 3.9,
          iron: "16%"
        },
        {
          to: "Jelly bean",
          direction: "left",
          from: 0.0,
          amount: 94,
          protein: 0.0,
          iron: "0%"
        },
        {
          to: "Lollipop",
          direction: "left",
          from: 0.2,
          amount: 98,
          protein: 0,
          iron: "2%"
        },
        {
          to: "Honeycomb",
          direction: "left",
          from: 3.2,
          amount: 87,
          protein: 6.5,
          iron: "45%"
        },
        {
          to: "Donut",
          direction: "left",
          from: 25.0,
          amount: 51
        },
        {
          to: "KitKat",
          direction: "left",
          from: 26.0,
          amount: 65,
          protein: 7,
          iron: "6%"
        }
      ]
    };
  },
  methods: {
    getColor(direction) {
      if (direction === "right") return "red";
      else if (direction === "left") return "green";
      else return "orange";
    },
    addMoney() {
      if (this.coin > 0) {
        this.currentcoin = this.currentcoin + parseInt(this.coin);
        this.alert = true;
        setTimeout(() => {
          this.alert = false;
        }, 3000);
      } else {
        alert("Coin must be greater then 0");
      }
    }
  }
};
</script>