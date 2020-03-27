<template>
  <div class="full-width q-pa-lg">
    <q-table
        :data="itens"
        :columns="columns"
        :filter="filter"
        selection="multiple"
        :selected.sync="selected"
        row-key="id"
        hide-bottom
      >
        <q-tr slot="header" slot-scope="props">
          <q-th auto-width>
          </q-th>
          <q-th v-for="col in props.cols" :key="col.name" :props="props">
            {{ col.label }}
          </q-th>
        </q-tr>
        <template slot="body" slot-scope="props">
          <q-tr :props="props">
            <q-td auto-width>
              <q-checkbox color="primary" v-if="props.row.status.id !== 1 && !props.row.emVotacao && props.row.status.id !== 5 && props.row.status.id !== 12" v-model="props.selected" />
            </q-td>
            <q-td key="usuario" :props="props">{{ props.row.usuario }}</q-td>
            <q-td key="email" :props="props">{{ props.row.email }}</q-td>
            <q-td key="dataDeInclusao" :props="props">{{props.row.dataDeInclusao }}</q-td>
            <q-td key="dataDeAlteracao" :props="props">{{ props.row.dataDeAlteracao }}</q-td>
            <q-td key="regras" :props="props">{{ props.row.regras }}</q-td>
            <q-td key="status" :props="props">
              <span :style="`color: ${props.row.status === 'ATIVO' ? '#11ff00' : 'red' }`">
                <strong>{{ props.row.status }}</strong>
              </span>
            </q-td>
            <q-td key="acoes" :props="props">
              <q-btn flat round dense icon="more_horiz" />
            </q-td>
          </q-tr>
        </template>
      </q-table>
      <div class="row gutter-x-md justify-around">
        <div class="q-ma-md">
          <q-btn label="Primeiro" disabled />
          <q-btn label="Anterior" disabled />
          <q-btn label="1" color="pink" />
          <q-btn label="Próximo" disabled />
          <q-btn label="Último" disabled />
        </div>
      </div>
  </div>
</template>

<script>
import userList from 'assets/mock/userList'
export default {
  name: 'GridUserList',
  props: ['filtro'],
  created () {
    this.itens = userList
  },
  data () {
    return {
      filter: '',
      itens: [],
      serverPagination: {
        page: 1,
        rowsNumber: 3 // specifying this determines pagination is server-side
      },
      columns: [
        { name: 'usuario', label: 'USUÁRIO', field: 'usuario', align: 'center' },
        { name: 'email', label: 'EMAIL', field: 'email', align: 'left' },
        { name: 'dataDeInclusao', label: 'DATA DE INCLUSÃO', field: 'dataDeInclusao', align: 'center' },
        { name: 'dataDeAlteracao', label: 'DATA DE ALTERAÇÃO', field: 'dataDeAlteracao', align: 'center' },
        { name: 'regras', label: 'REGRAS', field: 'regras', align: 'center' },
        { name: 'status', label: 'STATUS', field: 'status', align: 'center' },
        { name: 'acoes', label: 'AÇÕES', field: 'acoes', align: 'center' }
      ],
      selected: []
    }
  },
  watch: {
    filtro: function (value) {
      this.filter = value
    }
  }
}
</script>
