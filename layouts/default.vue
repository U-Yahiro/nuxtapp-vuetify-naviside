<template>
  <div>
    <v-app dark prominent app>
      <v-navigation-drawer
        v-model="drawer"
        color="rgba(15,39,62,1);"
        :mini-variant.sync="miniVariant"
        permanent
        :clipped="clipped"
        fixed
        app
        dark
        ><v-list-item class="px-2">
          <v-list-item-avatar>
            <!-- <v-img src="https://randomuser.me/api/portraits/men/85.jpg"></v-img> -->
            <v-icon>mdi-account-circle</v-icon>
          </v-list-item-avatar>

          <v-list-item-title>John Leider</v-list-item-title>

          <v-btn icon @click.stop="miniVariant = !miniVariant">
            <v-icon>mdi-chevron-left</v-icon>
          </v-btn>
        </v-list-item>

        <v-divider></v-divider>
        <naviList />
        <template v-for="nav_list in nav_lists">
          <v-list-item
            v-if="!nav_list.lists"
            :to="nav_list.link"
            :key="nav_list.name"
          >
            <v-list-item-icon>
              <v-icon>{{ nav_list.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>
                {{ nav_list.name }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list-group
            v-else
            no-action
            :prepend-icon="nav_list.icon"
            :key="nav_list.name"
            v-model="nav_list.active"
          >
            <template v-if="show"
              ><span class="point"> <v-badge color="pink" dot></v-badge></span>
            </template>
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title>
                  {{ nav_list.name }}
                </v-list-item-title>
              </v-list-item-content>
            </template>
            <v-list-item
              v-for="list in nav_list.lists"
              :key="list.name"
              :to="list.link"
            >
              <v-list-item-title>
                {{ list.name }}
                <template v-if="show"
                  ><span class="alert"
                    ><v-badge color="pink" content="3"></v-badge
                  ></span>
                </template>
              </v-list-item-title>
            </v-list-item>
          </v-list-group>
        </template>
      </v-navigation-drawer>
      <v-app-bar :clipped-left="clipped" fixed app>
        <v-btn icon @click.stop="miniVariant = !miniVariant">
          <v-icon>mdi-{{ `chevron-${miniVariant ? "right" : "left"}` }}</v-icon>
        </v-btn>
        <v-btn icon @click.stop="clipped = !clipped">
          <v-icon>mdi-arrow-split-vertical</v-icon>
        </v-btn>
        <v-btn icon @click.stop="fixed = !fixed">
          <v-icon>mdi-arrow-split-horizontal</v-icon>
        </v-btn>
        <!-- <v-toolbar-title v-text="title" /> -->
        <v-spacer />
        <Logo />
        <v-icon>mdi-account</v-icon>
        <v-divider class="mx-4" vertical />
        <v-btn icon @click.stop="rightDrawer = !rightDrawer">
          <v-icon>mdi-menu</v-icon>
        </v-btn>
      </v-app-bar>
      <v-main>
        <v-container>
          <nuxt />
        </v-container>
      </v-main>
      <v-navigation-drawer
        v-model="rightDrawer"
        :right="right"
        temporary
        fixed
        color="rgba(15,39,62,1);"
        dark
      >
        <v-list>
          <v-list-item @click.native="right = !right">
            <v-list-item-action>
              <v-icon light>
                mdi-repeat
              </v-icon>
            </v-list-item-action>
            <v-list-item-title>Switch drawer (click me)</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-footer :absolute="!fixed" app>
        <span>&copy; {{ new Date().getFullYear() }}</span>
      </v-footer>
    </v-app>
  </div>
</template>

<script>
import Logo from "~/components/Logo";
import naviList from "~/components/naviList";

export default {
  components: {
    Logo,
    naviList
  },
  data() {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      show: true,
      show: false,
      nav_lists: [
        {
          name: "ダッシュボード",
          icon: "mdi-view-dashboard",
          link: "/"
        },
        {
          name: "xxxxx",
          icon: "mdi-bell",
          link: "/"
        },
        {
          name: "発注アラート",
          icon: "mdi-bell",
          active: false,
          link: "/",
          lists: [
            {
              name: "xxxxxxxxxxxx",
              link: "/quick-start"
            },
            {
              name: "Pre-made layouts",
              link: "/pre-made-layouts"
            }
          ]
        },
        {
          name: "発注アラート",
          icon: "mdi-note-text-outline",
          active: false,
          link: "",
          lists: [
            {
              name: "Quick Start",
              link: "/quick-start"
            },
            {
              name: "Pre-made layouts",
              link: "/pre-made-layouts"
            }
          ]
        },
        {
          name: "発注アラート",
          icon: "mdi-book",
          active: false,
          link: "",
          lists: [
            {
              name: "Quick Start",
              link: "/quick-start"
            },
            {
              name: "Pre-made layouts",
              link: "/pre-made-layouts"
            }
          ]
        },
        {
          name: "発注アラート",
          icon: "mdi-bell",
          active: false,
          link: "",
          lists: [
            {
              name: "Quick Start",
              link: "/quick-start"
            },
            {
              name: "Pre-made layouts",
              link: "/pre-made-layouts"
            }
          ]
        },
        {
          name: "Styles & animations",
          icon: "mdi-palette",
          link: "",
          active: false,
          lists: [
            {
              name: "Colors",
              link: "/colors"
            },
            {
              name: "Content",
              link: "/content"
            },
            {
              name: "Display",
              link: "/display"
            }
          ]
        },
        {
          name: "UI Components",
          icon: "mdi-view-dashboard",
          link: "/inspire"
        },
        {
          name: "Directives",
          icon: "mdi-function",
          link: "/"
        },
        {
          name: "Preminum themes",
          icon: "mdi-vuetify",
          link: "/preminum_themes"
        }
      ],
      miniVariant: true,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js"
    };
  }
};
</script>
<style scoped>
.theme--light.v-toolbar.v-sheet {
  background-color: rgb(15, 39, 62);
  color: white;
}

.v-application a {
  color: #00c58e;
}

.theme--light.v-icon {
  color: white;
}

.v-application .primary--text {
  color: white !important;
  caret-color: #00c58e !important;
}

.point {
  inset: auto auto calc(100% - 2px) calc(100% - 2px);
  margin-left: 29px;
  margin-top: 0px;
  margin-bottom: -28px;
}
.alert {
  margin-left: 21px;
}
</style>
