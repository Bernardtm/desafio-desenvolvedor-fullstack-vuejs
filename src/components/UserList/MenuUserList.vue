<template>
  <div class="row q-gutter-md full-width">
    <div>
      <q-btn
        icon="settings"
      />
    </div>
    <div>
      <q-btn
        icon="security"
      />
      <q-btn
        icon="person"
      />
    </div>
    <div>
      <q-input color="grey-3" outlined v-model="text" label="Pesquisar...">
        <template v-slot:append>
          <q-icon name="search" />
        </template>
      </q-input>
    </div>
    <div>
      <q-btn
        icon="tune"
      />
      <q-btn
        label="INCLUIR USUÁRIO"
        color="pink"
      />
      <q-btn
        flat
        icon="home"
      />
      <q-btn
        flat
        icon="settings"
      />
      <q-btn
        flat
        icon="power_settings_new"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'MenuUserList'
}
</script>
