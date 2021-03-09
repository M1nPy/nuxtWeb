<template>
  <v-app>
    <v-app-bar color="primary" dark app clipped-right>
      <v-toolbar-title>M1nPy</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items v-for="n in nav_lists" :key="n.name">
        <v-btn class="hidden-sm-and-down" text :to="n.link" :nuxt="true">{{
          n.name
        }}</v-btn>
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
            :nuxt="true"
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
    <v-footer dark padless>
      <v-card class="flex">
        <v-card-title class="py-2">
          <strong>© M1nPy</strong>
          <v-spacer></v-spacer>
          2021-{{ new Date().getFullYear() }}
        </v-card-title>
        <v-spacer></v-spacer>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      nav_lists: [
        {
          name: 'Top',
          icon: 'mdi-vuetify',
          link: '/',
        },
        {
          name: 'Story',
          icon: 'mdi-cogs',
          link: '/Story',
        },
        {
          name: 'Character',
          icon: 'mdi-account-multiple',
          link: '/Character',
        },
        {
          name: 'Gallery',
          icon: 'mdi-palette',
          link: '/Gallery',
        },
        {
          name: 'Download',
          icon: 'mdi-arrow-collapse-down',
          link: '/Download',
        },
        {
          name: 'Spec',
          icon: 'mdi-package-variant-closed',
          link: '/Spec',
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
