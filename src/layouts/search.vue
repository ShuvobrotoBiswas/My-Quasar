<template>
  <q-layout view="hHh Lpr fFf"> <!-- Be sure to play with the Layout demo on docs -->

    <!-- (Optional) The Header -->
    <q-header elevated class="row justify-center">
      <q-toolbar class="col">
        
        <q-toolbar-title>
          Breaking Bad API Example
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs>
        <q-route-tab  :to="{name: 'profile' , params: {id: 1}}" replace label="CSE"/>
        <q-route-tab  :to="{name: 'profile' , params: {id: 2}}" replace label="EEE"/>
        <q-route-tab  :to="{name: 'profile' , params: {id: 'random'}}" replace label="Random"/>
      </q-tabs>
    </q-header>

    <!-- (Optional) The Footer -->
    

    <!-- (Optional) A Drawer; you can add one more with side="right" or change this one's side -->
   

    <q-page-container>
      <!-- This is where pages get injected -->
      <router-view :key="$route.params.id"/>
    </q-page-container>

  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  // name: 'LayoutName',

  meta: {
    title: "My Quasar  App"
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
}
</script>
<style lang="scss" scoped>


</style>