<template>
 <!-- toolbar and navbar -->
  <nav>
    <v-toolbar flat app>
      <v-toolbar-side-icon @click.stop="drawer = !drawer" class="grey--text"></v-toolbar-side-icon>
      <v-toolbar-title class="text-uppercase grey--text">
        <span class="font-weight-light">Good</span>
        <span>Reads</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>

 <!-- dropdown menu -->
      <v-menu offset-y>
        <v-btn flat slot="activator" color="grey">
          <v-icon>expand_more</v-icon>
          <span>Menu</span>
        </v-btn>
        <v-list>
          <v-list-tile v-for="link in links" :key="link.text" router :to="link.route">
            <v-list-tile-title>{{ link.text }}</v-list-tile-title>
          </v-list-tile>
        </v-list> 
      </v-menu>

 <!-- Popup dialog box -->
      <v-flex>
        <Popup />
      </v-flex>
    </v-toolbar>

 <!-- User Info Card -->
    <v-navigation-drawer app v-model="drawer" class="primary">
       <v-layout column align-center>
        <v-flex class="mt-5">
          <v-avatar size="100">
            <img class="text-lg-center" src="/user.png">
          </v-avatar>
          <p class="white--text subheading mt-1">Guest User</p>
        </v-flex>
      </v-layout>
      <v-list>
        <v-list-tile v-for="link in links" :key="link.text" router :to="link.route">
          <v-list-tile-action>
            <v-icon class="white--text">{{ link.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title class="white--text">{{ link.text }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>

  </nav>
</template>

<script>
import Popup from './Popup.vue'
export default {
  components: { Popup },
  data() {
    return {
      drawer: false,
      links: [
        { icon: 'dashboard', text: 'Dashboard', route: '/' },
        { icon: 'folder', text: 'ReadPad', route: '/projects' },
        { icon: 'person', text: 'Authors', route: '/team' },
      ]
    }
  }
}
</script>

<style>

</style>
