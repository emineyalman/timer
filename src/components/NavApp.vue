<template>
    <div>
      <v-app-bar :elevation="2">
        <template v-slot:prepend>
          <v-app-bar-nav-icon
            @click="isDrawerOpen = !isDrawerOpen"
          ></v-app-bar-nav-icon>
        </template>
        <v-app-bar-title>Timer</v-app-bar-title>
      </v-app-bar>
  
      <v-navigation-drawer v-model="isDrawerOpen">
        <v-list-item title="Laps"></v-list-item>
        <v-divider></v-divider>
        <v-list-item v-for="(lap, index) in laps" :key="index">
          Lap {{ index + 1 }}: {{ lap }}
        </v-list-item>
      </v-navigation-drawer>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isDrawerOpen: false,
      };
    },
    props: ["laps"]
  };
  </script>
  