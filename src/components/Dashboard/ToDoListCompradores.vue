<template>
  <div class="todo_compradores">
    <h2>Histórico de compradores</h2>

    <table class="table_compradores">
      <thead>
        <tr>
          <th>ID</th>
          <th>Data</th>
          <th>Nome</th>
          <th>Localização</th>
          <th>Valor</th>
          <th>Situação</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="{ id, data, nome, localizacao, valor, situacao  } in historicoComprador" :key="id">
          <td>#{{ id}}</td>
          <td>{{ data }}</td>
          <td>{{ nome }}</td>
          <td>{{ localizacao }}</td>
          <td>R${{ valor }}</td>
          <td class="status_comprador">
            <span :class="situacao"></span>
          {{ situacao }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "ToDoListCompradores",
  data() {
    return {
      historicoComprador : []
    };
  },

  methods:{
    async getTodoCompradores(){
      try{
        const dataFetch = await axios("http://localhost:3000/ToList_Compradores")
        this.historicoComprador = dataFetch.data.compradores;
      }catch(ERROR){
        console.error("Erro ao buscar dados de Compradores: ", ERROR);
      }

    }
  },

  mounted(){
    this.getTodoCompradores()
  }
};
</script>

<style scoped>
.todo_compradores {
  border-radius: 1rem;
  background: var(--white);
  box-shadow: 0 1rem 1.2rem rgba(0, 0, 0, 0.1);
  height: 20rem;
  overflow-y: scroll;
  padding: 2.5rem 2rem 0 2rem;
  margin-top: 2rem;
}

.todo_compradores h2 {
  color: var(--dark);
  font-family: var(--main-font);
  font-size: 2rem;
  font-style: normal;
  margin-bottom: 2rem;
}

.todo_compradores .table_compradores {
  width: 100%;
}

.todo_compradores .table_compradores thead {
  width: 100%;
  margin-bottom: 2rem;
}
.todo_compradores .table_compradores thead tr {
  width: 100%;
}

.todo_compradores .table_compradores thead tr th {
  color: var(--dark);
  font-family: var(--main-font);
  font-style: normal;
  font-size: 1.6rem;
  text-align: left;
}

.todo_compradores .table_compradores tbody tr {
  text-align: left;
}

.todo_compradores .table_compradores tbody tr td {
  color: #6a6969;
  font-size: 1.4rem;
  font-family: var(--main-font);
  font-style: normal;
  font-weight: 500;
  text-align: left;
  padding: 1.5rem 0 1rem 0;
  border-bottom: .2rem solid var(--light-gray);
}

.todo_compradores .table_compradores tbody tr .status_comprador{
  display: flex;
  align-items: center;
}

.Aprovado{
  background: var(--success);
}

.Reprovado{
  background: var(--error);
}

.Analise{
  background: var(--warning);
}

.todo_compradores .table_compradores tbody tr .status_comprador .Aprovado,
.todo_compradores .table_compradores tbody tr .status_comprador .Reprovado,
.todo_compradores .table_compradores tbody tr .status_comprador .Analise{
  width: .8rem;
  height: .8rem;
  display: block;
  border-radius: 50%;
  margin-right: .8rem;
}
</style>