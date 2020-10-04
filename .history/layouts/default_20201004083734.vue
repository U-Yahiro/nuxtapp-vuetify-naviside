<template>
  <v-app color="rgba(15,39,62,1);" dark app>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant.sync="mini"
      permanent
      :clipped="clipped"
      fixed
      app
      dark
      color="rgba(15,39,62,1);"
      ><v-list-item class="px-2">
        <v-list-item-avatar>
          <v-img src="https://randomuser.me/api/portraits/men/85.jpg"></v-img>
        </v-list-item-avatar>

        <v-list-item-title>John Leider</v-list-item-title>

        <v-btn icon @click.stop="mini = !mini">
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
      </v-list-item>

      <v-divider></v-divider>
      <!-- <naviList /> -->
      <template v-for="nav_list in nav_lists">
        <v-list-item
          v-if="!nav_list.lists"
          :to="nav_list.link"
          :key="nav_list.name"
          @click="menu_close"
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
            </v-list-item-title>
          </v-list-item>
        </v-list-group>
      </template>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <!-- <v-app-bar-nav-icon @click.stop="drawer = !drawer" /> -->
      <v-btn icon @click.stop="mini = !mini">
        <v-icon>mdi-{{ `chevron-${miniVariant ? "right" : "left"}` }}</v-icon>
      </v-btn>
      <v-btn icon @click.stop="clipped = !clipped">
        <v-icon>mdi-application</v-icon>
      </v-btn>
      <v-btn icon @click.stop="fixed = !fixed">
        <v-icon>mdi-minus</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>mdi-menu</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
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
</template>

<script>
import NaviList from "~/layouts/naviList";

export default {
  components: {
    NaviList,

  },
  data() {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      supports: [
        {
          name: "Consulting and suppourt",
          icon: "mdi-vuetify",
          link: "/consulting-and-support"
        },
        {
          name: "Discord community",
          icon: "mdi-discord",
          link: "/discord-community"
        },
        {
          name: "Report a bug",
          icon: "mdi-bug",
          link: "/report-a-bug"
        },
        {
          name: "Github issue board",
          icon: "mdi-github-face",
          link: "/guthub-issue-board"
        },
        {
          name: "Stack overview",
          icon: "mdi-stack-overflow",
          link: "/stack-overview"
        }
      ],
      nav_lists: [
        {
          name: "Getting Started",
          icon: "mdi-speedometer",
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
          name: "Customization",
          icon: "mdi-cogs",
          link: "/customization"
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
      mini: true,
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
<style scoped>
.v-toolbar__content {
  align-items: center;
  display: flex;
  position: relative;
  z-index: 0;
  background-color: "rgba(15,39,62,1);!important";
}

.v-toolbar__content, .v-toolbar__extension {
    align-items: center;
    display: flex;
    position: relative;
    z-index: 0;
    background-color: rgb(15, 39, 62);
}
v-app {
  background-color: "rgba(15,39,62,1);!important";
} 

v-a {
    color: var(--v-primary-base);
    background-color: var(--v-accent-lighten2);
}
</style>
