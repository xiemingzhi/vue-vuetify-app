<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-app-bar-nav-icon v-if="!isNotHome()" @click="drawer = !drawer" />
      <v-btn v-if="isNotHome()" @click="goHome()" icon>
        <v-icon>mdi-chevron-left</v-icon>
      </v-btn>
      <v-toolbar-title>Toolbar</v-toolbar-title>
      <v-spacer></v-spacer>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list dense>
        <v-list-item to="/todos">
          <v-list-item-action>
            <v-icon>mdi-exit-to-app</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Todos</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <router-view/>
    </v-content>

    <v-tabs
      v-model="tab"
      background-color="deep-purple accent-4"
      centered
      dark
      icons-and-text
    >
      <v-tabs-slider></v-tabs-slider>
      <v-tab href="#tab-1">
        Recents
        <v-icon>mdi-phone</v-icon>
      </v-tab>
      <v-tab href="#tab-2">
        Favorites
        <v-icon>mdi-heart</v-icon>
      </v-tab>
      <v-tab href="#tab-3">
        Nearby
        <v-icon>mdi-account-box</v-icon>
      </v-tab>
    </v-tabs>

  </v-app>
</template>

<script>
//import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    //HelloWorld,
  },

  data: () => ({
    //
    drawer: null,
    drawerRight: null,
    right: false,
    left: false,
  }),

  methods: {
    isNotHome() {
      return this.$router.history.current["path"] !== "/";
    },
    goTodos() {
      this.drawer = null
      return this.$router.push("/todos")
    },
    goHome() {
      this.drawer = null
      return this.$router.push("/")
    }
  },

};
</script>
