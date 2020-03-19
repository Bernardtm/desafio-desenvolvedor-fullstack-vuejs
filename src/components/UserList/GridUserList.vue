<template>
  <div>
    <!-- <q-table
        no-data-label="Nenhum item foi filtrado"
        rows-per-page-label="Linhas por página:"
        :data="itens"
        :columns="columns"
        :filter="filter"
        selection="multiple"
        :selected.sync="selected"
        row-key="id"
      >
        <q-tr slot="header" slot-scope="props">
          <q-th auto-width>
            <q-toggle
              v-model="destaque"
              v-if="itens.length > 0"
              checked-icon="done_all"
              unchecked-icon="check"
              color="primary"
              @input="selectAll()"
            />
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
            <q-td key="item" :props="props">{{ props.row.item }}</q-td>
            <q-td key="descricaoItem" :props="props">{{ props.row.descricaoItem.substring(0,28) }} ...
              <q-tooltip>{{ props.row.descricaoItem }}</q-tooltip>
            </q-td>
            <q-td key="nomePessoa" :props="props">
               {{props.row.nomePessoa}}
            </q-td>
            <q-td key="situacao" :props="props">
              <q-chip dense color="warning" icon="check" v-if="props.row.status.id == 0">{{ props.row.status.nome }}</q-chip>
              <q-chip dense color="grey" icon="check" v-if="props.row.status.id == 2">{{ props.row.status.nome }}</q-chip>
              <q-chip dense color="blue" icon="done_all" v-if="props.row.status.id == 3">{{ props.row.status.nome }}</q-chip>
              <q-chip dense color="info" icon="how_to_vote" v-if="props.row.status.id == 1">{{ props.row.status.nome }}</q-chip>
              <q-chip dense color="dark" icon="clear"  v-if="props.row.status.id == 5">{{ props.row.status.nome }}</q-chip>
              <q-chip dense color="green" icon="visibility"  v-if="props.row.status.id == 4">{{ props.row.status.nome }}</q-chip>
            </q-td>
            <q-td key="acoes" :props="props">
              <q-btn flat round  title="Solicitou Vista" @click.native="itemModal = props.row; $refs.modalSolicitacaoDeVista.show()" size="md"
                     v-if="props.row.solicitacaoVista && props.row.status.id !== 4">
                <q-icon name="pan_tool" color="green" size="20"/>
              </q-btn>
               <q-chip dense color="dark" v-if="props.row.extraPauta">EXTRA PAUTA</q-chip>
                <q-btn flat round dense icon="more_vert">
                  <q-popover>
                    <q-list link>
                      <q-item v-close-overlay v-if="!props.row.emVotacao && props.row.status.id !== 1">
                      <q-btn icon="list"
                             flat
                             @click.native="itemModal = props.row; $refs.modalEnquete.toggle();"
                             size="sm" dense>
                             &nbsp;Enquete &nbsp;&nbsp;&nbsp;
                       </q-btn>
                      </q-item>
                      <q-item v-if="props.row.temEnquete && props.row.status.id !== 1">
                        <q-btn icon="clear"
                              color="red"
                              flat
                              @click.native="props.row.temEnquete = false; exluiEnquete(props.row);"
                              size="sm" dense>
                              &nbsp;Excluir Enquete &nbsp;&nbsp;&nbsp;
                        </q-btn>
                      </q-item>

                      <q-item v-close-overlay v-if="props.row.status.id === 1">
                        <q-btn icon="touch_app"
                              flat
                              @click.native="$refs.modalVotacaoDeclaracao.toggle(props.row.id)"
                              size="sm" dense>
                              &nbsp; Declarar Voto
                        </q-btn>
                      </q-item>
                      <q-item v-close-overlay>
                       <q-btn icon="help"
                              flat
                              @click.native="itemModal = props.row; $refs.modalItemGrid.show(); perguntaOuObservacao = 'Pergunta'"
                              size="sm" dense>
                              &nbsp; Pergunta
                        </q-btn>
                      </q-item>
                      <q-item v-close-overlay>
                           <q-btn icon="comment"
                                  flat
                                  @click.native="itemModal = props.row; $refs.modalItemGrid.show(); perguntaOuObservacao = 'Observação'"
                                  size="sm" dense>
                             &nbsp;Observação
                           </q-btn>
                      </q-item>
                    </q-list>
                  </q-popover>
                </q-btn>
            </q-td>
          </q-tr>
        </template>
        <template slot="top-right" slot-scope="props">
          <q-search hide-underline v-model="filter" v-if="itens.length > 0"  color="dark" float-label="Filtrar no grid"/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          <combo-acoes @resetGrid="resetGrid" :indicadores="indicadores[idReuniao]" :statusVotacao="statusVotacao" @updateStatus="updateStatus" :reuniao="reuniao[idReuniao]" v-if="selected.length > 0" :itens="selected"></combo-acoes>
          <combo-filtro @filtro="pesquisaItens" :idsPautas="idsPautas" :idPauta="idPauta" :idExtraPauta="idExtraPauta" v-if="selected.length === 0"></combo-filtro>
          <q-btn round flat color="primary" @click.native="$refs.modalAdicionaItem.toggle()"  icon="add" />
        </template>
        <template slot="top-left" slot-scope="props">
        <combo-acao-votacao v-if="reuniao[idReuniao].statusPainelConselheiro === 'votacao'"
                              @updateStatus="updateStatus"
                              @resetGrid="resetGrid"
                              :statusVotacao="statusVotacao"
                              :itens="selected"
                              :participantes="participantes[idReuniao]"
                              :reuniao="reuniao[idReuniao]" ></combo-acao-votacao>
        </template>
      </q-table> -->
    (SELECT BUTTON)| USUÁRIO | EMAIL | DATA DE INCLUSÃO | DATA DE ALTERAÇÃO | REGRAS | STATUS | AÇÕES
        Primeiro Anterior  (pagina atual) Próximo  Último
  </div>
</template>

<script>
export default {
  name: 'GridUserList'
}
</script>
