<template>

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
