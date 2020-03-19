<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-grey-3 text-grey-9">
      <menu-user-list />
    </q-header>
    <q-page-container>
      <q-page class="flex flex-center">
        <grid-user-list/>
      </q-page>
    </q-page-container>
    <q-footer elevated class="bg-black">
      <footer-live />
    </q-footer>
  </q-layout>
</template>

<script>
import MenuUserList from 'components/UserList/MenuUserList'
import GridUserList from 'components/UserList/GridUserList'
import FooterLive from 'components/Footer/FooterLive'
export default {
  name: 'PageIndex',
  components: {
    MenuUserList,
    GridUserList,
    FooterLive
  }
}
</script>
