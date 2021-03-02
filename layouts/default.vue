<template>
  <v-app>
    <v-app-bar color="primary" dark app clipped-right>
      <v-toolbar-title>M1nPy</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn class="hidden-sm-and-down" text to="/">Home</v-btn>
      </v-toolbar-items>
      <v-toolbar-items>
        <v-btn class="hidden-sm-and-down" text to="/About">About</v-btn>
      </v-toolbar-items>
      <v-toolbar-items>
        <v-btn class="hidden-sm-and-down" text to="/Graphic">Graphic</v-btn>
      </v-toolbar-items>
      <v-toolbar-items>
        <v-btn class="hidden-sm-and-down" text to="/Links">Links</v-btn>
      </v-toolbar-items>
      <v-app-bar-nav-icon
        class="hidden-md-and-up"
        @click="drawer = !drawer"
      ></v-app-bar-nav-icon>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      class="hidden-md-and-up"
      app
      right
      clipped
    >
      <v-container>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title">
              Navigation lists
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list dense nav>
          <v-list-item
            v-for="nav_list in nav_lists"
            :key="nav_list.name"
            :to="nav_list.link"
          >
            <v-list-item-icon>
              <v-icon>{{ nav_list.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ nav_list.name }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-container>
    </v-navigation-drawer>

    <v-main class="px-0">
      <nuxt />
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      nav_lists: [
        {
          name: 'Home',
          icon: 'mdi-vuetify',
          link: '/',
        },
        {
          name: 'About',
          icon: 'mdi-cogs',
          link: '/About',
        },
        {
          name: 'Graphic',
          icon: 'mdi-palette',
          link: '/Graphic',
        },
        {
          name: 'Links',
          icon: 'mdi-view-dashboard',
          link: '/Links',
        },
      ],
    }
  },
}
</script>
