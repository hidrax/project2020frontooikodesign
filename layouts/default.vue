<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      fixed
      clipped
      right
      expand-on-hover
      mini-variant
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar clipped-right app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-tooltip bottom>
        <template v-slot:activator="{ on }">
          <v-btn icon small color="warning accent-2 white--text" v-on="on">
            <v-icon style="transform: rotate(180deg);"
              >mdi-logout-variant
            </v-icon>
          </v-btn>
        </template>
        <span>خروج</span>
      </v-tooltip>

      <v-progress-linear
        :active="false"
        indeterminate
        absolute
        bottom
        :color="$vuetify.theme.dark ? 'red' : 'primary'"
      ></v-progress-linear>
    </v-app-bar>
    <v-content>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
      id="footer"
      class="font-weight-medium justify-end align-end"
      style="height: 140px; background: url('images/application/repeat-1920-140.png')"
    >
      <v-col class="text-center" cols="12" style="color:#fff;">
        &copy; {{ new Date().getFullYear() }} — <strong>TOOTIKO</strong>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: true,
      items: [
        {
          icon: 'mdi-apps',
          title: 'خانه',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'صفحه دوم',
          to: '/inspire'
        }
      ],
      title: 'طوطیکو'
    }
  },
  beforeCreate() {
    this.$vuetify.rtl = true
  }
}
</script>
