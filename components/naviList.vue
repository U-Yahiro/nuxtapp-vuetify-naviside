<template>
  <div>
    <v-expansion-panels
      color="rgba(15,39,62,1);"
      v-model="panel"
      :disabled="disabled"
      multiple
      focusable
    >
      <v-expansion-panel>
        <v-expansion-panel-content>
          <v-icon>mdi-view-dashboard</v-icon>1,000 miles of wondeSome content
        </v-expansion-panel-content>
        <v-expansion-panel-content>
          Some contents
        </v-expansion-panel-content>
      </v-expansion-panel>
      

      <v-expansion-panel>
        <v-expansion-panel-header>Panel 2</v-expansion-panel-header>
        <v-expansion-panel-content>
          Some content
        </v-expansion-panel-content>
        <v-expansion-panel-content>
          Some content
        </v-expansion-panel-content>
      </v-expansion-panel>

      <v-expansion-panel>
        <v-expansion-panel-header>Panel 3</v-expansion-panel-header>
        <v-expansion-panel-content>
          Some content
        </v-expansion-panel-content>
        <v-expansion-panel-content>
          Some content
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  
    <v-card class="px-2" max-width="344" color="rgba(15,39,62,1);">
      <v-card-title>
        <v-icon>mdi-account-circle</v-icon>
        Top western road trips
      </v-card-title>

      <v-card-subtitle>
        <v-icon>mdi-view-dashboard</v-icon>1,000 miles of wonder
      </v-card-subtitle>

      <v-card-actions>
        <v-btn color="orange lighten-2" text>
          Explore
        </v-btn>
      </v-card-actions>
    </v-card>
    <v-card class="px-2" max-width="344" color="rgba(15,39,62,1);">
      <v-card-title>
        <v-icon>mdi-account-circle</v-icon>
        Top western road trips
      </v-card-title>

      <v-card-subtitle>
        <v-icon>mdi-account-circle</v-icon>1,000 miles of wonder
      </v-card-subtitle>

      <v-card-actions>
        <v-btn color="orange lighten-2" text>
          Explore
        </v-btn>

        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
            I'm a thing. But, like most politicians,
          </v-card-text>
          <v-divider></v-divider>

          <v-card-text>
            I'm a thing. But, like most politicians,
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
    <v-card class="px-2" max-width="344" color="rgba(15,39,62,1);">
      <v-card-title>
        <v-icon>mdi-account-circle</v-icon>
        Top western road trips
      </v-card-title>

      <v-card-subtitle>
        1,000 miles of wonder
      </v-card-subtitle>

      <v-card-actions>
        <v-btn color="orange lighten-2" text>
          Explore
        </v-btn>

        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
            I'm a thing. But, like most politicians,
          </v-card-text>
          <v-divider></v-divider>

          <v-card-text>
            I'm a thing. But, like most politicians,
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
    <v-card class="px-3" max-width="344" color="rgba(15,39,62,1);">
      <v-card-title>
        <v-icon>mdi-account-circle</v-icon>
        Top western road trips
      </v-card-title>

      <v-card-subtitle>
        1,000 miles of wonder
      </v-card-subtitle>

      <v-card-actions>
        <v-btn color="orange lighten-2" text>
          Explore
        </v-btn>

        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
            I'm a thing. But, like most politicians,
          </v-card-text>
          <v-divider></v-divider>

          <v-card-text>
            I'm a thing. But, like most politicians,
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      drawer: null,
      show: false,
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
      ]
    };
  }
};
</script>
<style scoped>
.v-expansion-panel-content__wrap {
    padding: 0 24px 16px;
    flex: 1 1 auto;
    max-width: 100%;
    background-color: "rgba(15,39,62,1) !important";
}
</style>
