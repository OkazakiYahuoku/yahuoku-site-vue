<template>
  <v-app>
    <v-main>
      <v-navigation-drawer
      v-model="drawer"
      color="basil"
      floating
      app
      style="z-index: 200;"
      >
      <v-divider></v-divider>
      <v-list>
        <v-list-item
          v-for="link in links"
          :key="link.icon"
          :to="link.to"
          link
        >
        <v-list-item-icon>
          <v-icon>{{ link.icon }}</v-icon>
        </v-list-item-icon>

      <v-list-item-content>
        <v-list-item-title>{{ link.name}}</v-list-item-title>
      </v-list-item-content>
      </v-list-item>
      </v-list>
      </v-navigation-drawer>

<!-- header -->

      <header class="layout-header" style="position: sticky; top: 0;">
        <v-card>
          <v-toolbar>
            <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="text-center justify-center py-6 basil--text">
              パーツショップタッキー
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <template v-slot:extension>
              <v-tabs
                v-model="tab"
                background-color="transparent"
                grow
              >
                <v-tab
                  v-for="item in links"
                  :key="item.name"
                  :to="item.to"
                >
                  {{ item.name }}
                </v-tab>
              </v-tabs>
            </template>
          </v-toolbar>
        </v-card>
      </header>
<!-- header _END_ -->

<!-- main-content _BEGIN_ -->
          <router-view/>
<!-- main-content _END_ -->

<!-- footer _BEGIN_ -->
      <footer class="layout-footer">
        <small>©︎ 2021 okazakiyahuoku Co.,Ltd.</small>
      </footer>
<!-- footer _END_ -->

    </v-main>
  </v-app>
</template>
<script>

export default {
  data: () => ({
    tab: null,
    drawer: null,
    links: [
      { name: 'お読みください', to: '/', icon: 'mdi-arrow-right-drop-circle' },
      { name: '送料一覧表', to: '/price_list', icon: 'mdi-grid' }
    ]
  }),
  components: {
  }
}
</script>
<style lang="scss" scoped>
/* Helper classes */
.basil--text {
  color: #356859 !important;
}
</style>
