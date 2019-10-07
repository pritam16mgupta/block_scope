<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-light">Block Scope</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn text>
          <router-link to="/wallet">Wallet</router-link>
        </v-btn>
        <v-btn text>
          <router-link to="/transaction">Transaction</router-link>
        </v-btn>
        <v-btn text>
          <router-link to="/blocks">Blocks</router-link>
        </v-btn>

        <v-menu transition="slide-y-transition" offset-y>
          <template v-slot:activator="{ on }">
            <!-- <v-btn class="purple" color="primary" dark v-on="on">Slide Y Transition</v-btn> -->
            <v-btn icon v-on="on">
              <v-icon>mdi-account</v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item>
              <v-list-item-title>{{username}}</v-list-item-title>
            </v-list-item>
            <v-list-item @click="logout">
              <v-list-item-title>LogOut</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </v-toolbar-items>
    </v-app-bar>

    <v-content>
      <!-- <HelloWorld/> -->
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    HelloWorld
  },
  data() {
    return {
      username: "Pritam Gupta"
    };
  },
  methods: {
    logout() {
      alert("logout");
    }
  }
};
</script>
