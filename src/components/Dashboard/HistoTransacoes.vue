<template>
  <section class="container_transacoes">
    <div class="histo_anual">
      <h3>Histórico de transações Semanal</h3>

      <div class="box_transacoes">
        <div class="box_transacao" v-for="item in histoSemanais" :key="item.id">
          <h4>{{ item.dia }}</h4>
          <strong :class="item.status">R$ {{ item.valor }}</strong>
        </div>
      </div>
    </div>
    <div class="histo_semanal">
      <h3>Histórico de transações Anual</h3>

      <div class="box_transacoes">
        <div class="box_transacao" v-for="item in histoAnuais" :key="item.id">
          <h4>{{ item.mes }}</h4>
          <strong :class="item.status">R$ {{ item.valor }}</strong>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  name: "HistoTransacoes",
  data() {
    return {
      histoAnuais: [],
      histoSemanais: [],
      status: true,
    };
  },
  
  methods: {
    async getHistoricoTransacoes() {
      try {
        const dataFetch = await axios({
          method: "GET",
          url: "http://localhost:3000/Dashboard",
        });

        this.histoAnuais = dataFetch.data.historico_transcoes_anuais;
        this.histoSemanais = dataFetch.data.historico_transcoes_semanais;
      } catch (ERROR) {
        console.error("Erro ao buscar dados de Transações: ", ERROR);
      }
    },
  },

  mounted() {
    this.getHistoricoTransacoes();
  },
};
</script>

<style scoped>
.container_transacoes {
  min-width: 100%;
  margin-top: 3.5rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2.5rem;
}

.histo_anual {
  width: 50%;
}

.histo_semanal {
  width: 50%;
}

.histo_anual,
.histo_semanal {
  height: 26rem;
  border-radius: 1rem;
  background: var(--white);
  box-shadow: 0 1rem 1.2rem rgba(0, 0, 0, 0.1);
}

.histo_anual h3,
.histo_semanal h3 {
  color: var(--dark);
  font-family: var(--main-font);
  font-size: 2rem;
  font-weight: 500;
  font-style: normal;
  margin: 2.4rem 0 2.4rem 3rem;
}

.histo_anual .box_transacoes,
.histo_semanal .box_transacoes {
  margin: 0 2.4rem 2.4rem 3rem;
}

.histo_anual .box_transacoes .box_transacao,
.histo_semanal .box_transacoes .box_transacao {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #9e6efe0f;
  border-radius: 0.6rem;
  padding: 1.3rem 1.4rem;
  margin-bottom: 1.5rem;
  cursor: pointer;
}

.histo_anual .box_transacoes .box_transacao h4,
.histo_semanal .box_transacoes .box_transacao h4 {
  color: var(--dark);
}

.histo_anual .box_transacoes .box_transacao h4,
.histo_semanal .box_transacoes .box_transacao h4,
.histo_anual .box_transacoes .box_transacao strong,
.histo_semanal .box_transacoes .box_transacao strong {
  font-family: var(--main-font);
  font-size: 1.4rem;
  font-style: normal;
}

.negativo {
  color: var(--error);
}

.positivo {
  color: var(--success);
}
</style>