<template>
  <v-app>
    <v-card class="overflow-hidden">
    <v-app-bar
     elevation="15"
      absolute
      color="blue"
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-spacer></v-spacer>
      <v-toolbar-title>Galeria "EY"</v-toolbar-title>
      <v-icon>
        mdi-image-multiple
      </v-icon>
      <v-spacer></v-spacer>
    </v-app-bar>
    <v-sheet
      id="scroll"
      class="overflow-y-auto mt-10"
    >
      <v-container>
      <v-main class="gg">
      <Gallery class="mt-10" />
    </v-main>
      </v-container>
    </v-sheet>
  </v-card>
    
    
  </v-app>
</template>

<script>
import Gallery from './components/Gallery';
export default {
  name: 'App',

  components: {
    Gallery,
  },
}
</script>

