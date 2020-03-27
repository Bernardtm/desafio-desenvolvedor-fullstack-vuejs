<template>
  <div class="row q-gutter-md justify-between q-pa-md">
    <div>
      <q-btn
        icon="settings"
      />
    </div>
    <div style="color: #EAEAEA; font-size: 30px; font-weight: bold;">
      |
    </div>
    <div>
      <q-btn
        icon="security"
        color="white"
        text-color="black"
      />
      <q-btn
        icon="person"
        color="deep-orange"
        glossy
      />
    </div>
    <div>
      <q-input
        color="grey-3"
        v-model="filter"
        label="Pesquisar..."
        @input="pesquisa"
      >
        <template v-slot:append>
          <q-icon name="search" />
        </template>
      </q-input>
    </div>
    <div class="row">
      <q-btn
        icon="tune"
        @click="opened = true"
      />
      <q-btn
        label="INCLUIR USUÁRIO"
        color="pink"
        icon="person"
      />
      <div style="color: #EAEAEA; font-size: 30px; font-weight: bold;">
        |
      </div>
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
    <q-dialog v-model="opened" :position="'right'">
      <q-card style="width: 550px; height: 1600px; background-color: #F5F5F5;">
        <div class="row q-pa-lg justify-between" style="background-color: white">
          <q-icon name="tune" size="sm" />
          <div>FILTROS</div>
          <q-btn icon="close" />
        </div>
        <div class="q-pa-md" style="color: #717171">
          Utilize os filtros abaixo para refinar os resultados da tabela,
          clique no botão APLICAR para salvar as alterações.
        </div>
        <div>
          <q-expansion-item
            expand-separator
            icon="date_range"
            label="TODAS AS DATAS DE INCLUSÃO"
            style="color: #D83468;"
          >
          </q-expansion-item>
        </div>
        <div>
          <q-expansion-item
            expand-separator
            icon="date_range"
            label="TODAS AS DATAS DE ALTERAÇÃO"
            style="color: #D83468;"
          >
          </q-expansion-item>
        </div>
        <div>
          <q-expansion-item
            expand-separator
            icon="hdr_strong"
            label="ATIVOS E INATIVOS"
            style="color: #D83468;"
          >
          </q-expansion-item>
        </div>
        <q-btn
          class="full-width"
          style="color: #D83468"
          label="APLICAR"
          disabled
        />
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
export default {
  name: 'MenuUserList',
  data () {
    return {
      opened: false,
      filter: ''
    }
  },
  methods: {
    pesquisa (value) {
      this.$emit('pesquisa', value)
    }
  }
}
</script>
