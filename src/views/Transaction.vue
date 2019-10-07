<template>
  <div>
    <v-container>
      <v-row>
        <v-col cols="12" sm="4">
          <p>Doctors</p>

          <v-overflow-btn
            class="my-2"
            :items="dropdown_edit"
            label="Doctors"
            editable
            item-value="text"
          ></v-overflow-btn>
        </v-col>
      </v-row>

      <template>
        <v-row align="center">
          <v-expansion-panels
            :accordion="accordion"
            :focusable=true
          >
            <v-expansion-panel v-for="(item,i) in 5" :key="i">
              <v-expansion-panel-header>Item</v-expansion-panel-header>
              <v-expansion-panel-content>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</v-expansion-panel-content>
            </v-expansion-panel>
          </v-expansion-panels>
        </v-row>
      </template>
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
      { text: "100%" },
      { text: "75%" },
      { text: "50%" },
      { text: "25%" },
      { text: "0%" }
    ]
  })
};
</script>