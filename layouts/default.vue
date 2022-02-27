<template>
  <v-app dark>
    <v-app-bar fixed app flat color="white">
      <v-container :fluid="fluid" :class="padding" class="py-0">
        <v-toolbar flat color="transparent">
          <v-menu
            offset-y
            v-model="menu"
            :nudge-width="300"
            :close-on-content-click="false"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                icon
                small
                v-on="on"
                v-bind="attrs"
                class="mr-3 hidden-sm-and-up"
              >
                <v-icon>mdi-menu</v-icon>
              </v-btn>
            </template>
            <v-list dense class="py-0" elevation="0">
              <v-list-item
                link
                :key="i"
                :to="route.to"
                v-for="(route, i) in routes"
                class="text-capitalize grey--text"
                active-class="text--darken-4 active"
              >
                <v-list-item-title>{{ route.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          <v-avatar :size="avatarSize" tile>
            <img src="@/assets/img/logo.png" alt="" />
          </v-avatar>

          <v-toolbar-items class="ml-sm-4 ml-lg-16 hidden-xs-only">
            <v-btn
              :key="i"
              depressed
              color="white"
              :to="route.to"
              v-for="(route, i) in routes"
              class="text-capitalize grey--text"
              active-class="text--darken-4 active"
            >
              {{ route.title }}
            </v-btn>
          </v-toolbar-items>

          <v-spacer />

          <v-btn
            rounded
            depressed
            :large="large"
            color="transparent"
            class="mr-3 text-capitalize"
            >Sign In</v-btn
          >
          <v-btn
            dark
            rounded
            depressed
            :large="large"
            color="#220070"
            class="text-capitalize"
            >Get Started</v-btn
          >
        </v-toolbar>
      </v-container>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer absolute app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",

  data: () => ({
    menu: false,
    routes: [
      {
        title: "Home",
        to: "/",
      },
      {
        title: "About",
        to: "/about",
      },
      {
        title: "FAQ",
        to: "/faq",
      },
      {
        title: "Contact Us",
        to: "/contactUs",
      },
    ],
  }),

  computed: {
    fluid() {
      switch (this.$vuetify.breakpoint.name) {
        case "xs":
          return true;
        case "sm":
          return true;
        case "md":
          return true;
        case "lg":
          return false;
        case "xl":
          return false;
      }
    },
    padding() {
      switch (this.$vuetify.breakpoint.name) {
        case "xs":
          return "px-0";
        case "sm":
          return "px-0";
        case "md":
          return "px-0";
      }
    },
    large() {
      switch (this.$vuetify.breakpoint.name) {
        case "xs":
          return false;
        case "sm":
          return false;
        case "md":
          return true;
        case "lg":
          return true;
        case "xl":
          return true;
      }
    },
    avatarSize() {
      switch (this.$vuetify.breakpoint.name) {
        case "xs":
          return 40;
        case "sm":
          return 40;
        case "md":
          return 50;
        case "lg":
          return 50;
        case "xl":
          return 50;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.active {
  &::before {
    display: none !important;
  }
}
</style>
