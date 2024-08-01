<template>
    <v-main color="primary">
      <v-container>
        <!-- row bileşeni yerine v-row kullanılmalı -->
        <v-row>
          <v-col cols="12" class="pa-3">
            <v-card>
              <v-card-title class="custom-title">
                {{ timer }}
              </v-card-title>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12" class="pa-3">
            <v-list-item class="success mb-3">
              <v-btn @click="$emit('start')" class="mx-4 my-1" color="#F50057">Start</v-btn>
              <v-btn @click="$emit('stop')" class="mx-4 my-1" color="#F4511E" large>Stop</v-btn>
              <v-btn @click="$emit('reset')" class="mx-4 my-1" color="#D500F9" large>Reset</v-btn>
              <v-btn @click="$emit('laps')" class="mx-4 my-1" color="#FDD835" large>Lap</v-btn>
            </v-list-item>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </template>
  
  <script>
  export default {
    props: ["timer"]
  };
  </script>
  
  <style scoped>
  .custom-title {
    font-size: 52px;
    margin: 0 auto;
  }
  .v-main {
    background: gray;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    margin: 0 auto;
  }
  </style>
  