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
    <v-footer
      dark
      class="footer"
      color="#362365"
      :app="$vuetify.breakpoint.name == 'xs' ? false : true"
      :absolute="$vuetify.breakpoint.name == 'xs' ? false : true"
    >
      <img class="img1" src="../assets/img/Frame 49.png" alt="" />
      <v-row justify="space-between" align="start" no-gutters>
        <v-col cols="12">
          <v-container class="py-16">
            <v-row justify="space-between" align="start">
              <v-col cols="12" sm="6" md="3" class="d-flex flex-column">
                <p class="text-h6 font-weight-light">Commpany</p>
                <span class="text-body-2 mt-3">Testimonials</span>
                <span class="text-body-2 mt-3">P2P Transaction</span>
                <span class="text-body-2 mt-3">FAQs</span>
                <span class="text-body-2 mt-3">Plog</span>
                <span class="text-body-2 mt-3">Careers</span>
              </v-col>
              <v-col cols="12" sm="6" md="3" class="d-flex flex-column">
                <p class="text-h6 font-weight-light">Support</p>
                <span class="text-body-2 mt-3">Security</span>
                <span class="text-body-2 mt-3">Fee Calculator</span>
                <span class="text-body-2 mt-3">Fraud Prevention</span>
                <span class="text-body-2 mt-3">Report Bug</span>
              </v-col>
              <v-col cols="12" sm="6" md="3" class="d-flex flex-column">
                <p class="text-h6 font-weight-light">Reach Us</p>
                <span class="text-body-2 mt-3"
                  ><v-icon class="mr-2">mdi-email-outline</v-icon>
                  contact@Trustpaddi.com</span
                >
                <span class="text-body-2 mt-3"
                  ><v-icon class="mr-2">mdi-phone-outline</v-icon>
                  +2349033275449</span
                >
                <span class="text-body-2 mt-3"
                  ><v-icon class="mr-2">mdi-map-marker-outline</v-icon>
                  Lagos</span
                >
              </v-col>
              <v-col cols="12" sm="6" md="3" class="d-flex flex-column">
                <p class="text-h6 font-weight-light">Stay up to data</p>
                <v-text-field
                  solo
                  flat
                  rounded
                  full-width
                  hide-details
                  background-color="#2E1E56"
                  placeholder="Enter address"
                  append-icon="mdi-send-outline mdi-rotate-315"
                ></v-text-field>

                <div class="d-flex justify-start align-start mt-6">
                  <v-btn fab small depressed color="#402E6D">
                    <img src="@/assets/img/u_facebook-f.png" alt="" />
                  </v-btn>
                  <v-btn fab small depressed color="#402E6D" class="mx-5">
                    <img src="@/assets/img/u_twitter.png" alt="" />
                  </v-btn>
                  <v-btn fab small depressed color="#402E6D">
                    <img src="@/assets/img/u_instagram-alt.png" alt="" />
                  </v-btn>
                </div>
              </v-col>
            </v-row>
          </v-container>
        </v-col>
        <v-col cols="12">
          <v-divider />
          <v-container class="d-flex justify-center">
            <span class="text-body-2"
              >&copy; {{ new Date().getFullYear() }} TrustPaddi. All rights
              reserved</span
            >
          </v-container>
        </v-col>
      </v-row>
      <img class="img2" src="../assets/img/Frame 49 2.png" alt="" />
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

.footer {
  overflow: hidden;
  .img1 {
    position: absolute;
    top: -5px;
    left: -5px;
    z-index: -1;
  }
  .img2 {
    position: absolute;
    bottom: -230px;
    right: 0;
    z-index: -1;
  }
}
</style>
