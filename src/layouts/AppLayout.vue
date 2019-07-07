<template>
  <q-layout view="lHh Lpr lFf">

    <q-header elevated>
      <q-toolbar class="bg-primary">
        <q-btn flat dense round @click="leftDrawerOpen = !leftDrawerOpen" aria-label="Menu">
          <q-icon name="menu" />
        </q-btn>

        <q-toolbar-title class="absolute-center">
          Todo App
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      bordered
      content-class="bg-secondary"
      :breakpoint="767.98"
    > 
      <q-list dark>
        <q-item-label header>Navigation</q-item-label>
        <q-item exact v-for="(item, index) in menu" :key="index" clickable :to="item.link">
          <q-item-section avatar>
            <q-icon :name="item.icon" />
          </q-item-section>
          <q-item-section>
            <q-item-label v-text="item.label" />
            <q-item-label caption v-text="item.description" />
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container class="bg-accent">
      <router-view />
    </q-page-container>

    <q-footer reveal elevated>
      <q-tabs
        dense
        v-model="tab"
        class="bg-secondary"
        active-color="brand"
        align="justify"
        :breakpoint="0"
      >
        <q-route-tab
          v-for="(item, index) in menu"
          :key="index"
          :icon="item.icon"
          :label="item.label"
          :to="item.link"
          exact
        />
      </q-tabs>
    </q-footer>

  </q-layout>
</template>

<script>
import { openURL } from 'quasar'

export default {
  name: 'AppLayout',
  data () {
    return {
      tab: null,
      leftDrawerOpen: this.$q.platform.is.desktop,
      menu: [
        {
          link: '/',
          icon: 'list',
          label: this.$t('menu.label.TODO'),
          description: this.$t('menu.description.TODO')
        },
        {
          link: '/settings',
          icon: 'settings',
          label: this.$t('menu.label.SETTINGS'),
          description: this.$t('menu.description.SETTINGS')
        },
      ]
    }
  },
  methods: {
    openURL
  }
}
</script>
