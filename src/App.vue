<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      fixed
      app
      width="220"
    >
      <v-list v-for="item in menu" :key="item.title">
        <v-list-tile @click="navigate(item.link)">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar color="primary" dark fixed app>
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title>HDFS Haystack</v-toolbar-title>
    </v-toolbar>
    <v-content>
      <v-fade-transition mode="out-in">
        <router-view></router-view>
      </v-fade-transition>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    menu: [{
      title: 'Download Image',
      icon: 'cloud_download',
      link: 'download-image'
    }, {
      title: 'Upload Image',
      icon: 'cloud_upload',
      link: 'upload-image'
    }]
  }),
  methods: {
    navigate (link) {
      this.$router.push({ name: link })
    }
  }
}
</script>

<style>
  html, body {
    overflow: auto !important;
  }
</style>
