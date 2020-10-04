<template>
<v-list nav dense>
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
</v-list>

    </v-container>
  </v-navigation-drawer>
    <v-app-bar color="primary" dark app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>

    </v-app-bar>
    <v-content>
      <router-view />
    </v-content>
</template>

<script>
export default {
  methods: {
    menu_close() {
      this.nav_lists.forEach(nav_list => (nav_list.active = false));
    }
  },
  data() {
    return {
      drawer: null,
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
          link: "/components"
        },
        {
          name: "Directives",
          icon: "mdi-function",
          link: "/directives"
        },
        {
          name: "Preminum themes",
          icon: "mdi-vuetify",
          link: "/preminum_themes"
        }
      ]
    };
  }
};
</script>
