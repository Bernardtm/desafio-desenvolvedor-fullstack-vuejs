<template>
  <div class="row q-gutter-md justify-between q-pa-md">
    <div>
      <q-btn
        icon="settings"
      />
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
      <q-dialog v-model="opened" :position="'right'">
        <q-card style="width: 550px; height: 900px; background-color: #F5F5F5;">
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
            <q-icon name="calendar" />
            <span style="color: #D83468;">TODAS AS DATAS DE INCLUSÃO</span>
          </div>
          <div>
            <q-icon name="calendar" />
            <span style="color: #D83468;">TODAS AS DATAS DE ALTERAÇÃO</span>
          </div>
          <div>
            <q-icon name="more_horiz" />
            <span style="color: #D83468;">ATIVOS E INATIVOS</span>
          </div>

          <q-btn label="APLICAR" disabled />
        </q-card>
      </q-dialog>
    </div>
    <div>
      <q-input
        color="grey-3"
        v-model="text"
        label="Pesquisar..."
      >
        <template v-slot:append>
          <q-icon name="search" />
        </template>
      </q-input>
    </div>
    <div>
      <q-btn
        icon="tune"
        @click="opened = true"
      />
      <q-btn
        label="INCLUIR USUÁRIO"
        color="pink"
        icon="person"
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
  name: 'MenuUserList',
  data () {
    return {
      opened: false
    }
  }
}
</script>
