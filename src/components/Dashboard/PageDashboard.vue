<template>
  <main class="container_main">
    <section>
      <PageHeader />
      <div class="container_info_geral">
        <HistoTransacoes />
        <PaineisVendas />
        <ToDoListCompradores />
      </div>
    </section>
  </main>
</template>

<script>
import PageHeader from '../PageHeader.vue';
import HistoTransacoes from './HistoTransacoes.vue';
import PaineisVendas from './PaineisVendas.vue';
import ToDoListCompradores from './ToDoListCompradores.vue';

export default {
  name : "PageDashboard",
  data(){

  },
  components:{
    PageHeader,
    HistoTransacoes,
    PaineisVendas,
    ToDoListCompradores
  }
};
</script>

<style scoped>
.container_main {
  width: 80%;
  display: flex;
  justify-content: center;
}

.container_main section{
  width: 85%;
}

.container_main section .container_info_geral{
  margin: 3.5rem 0;
}


</style>