<template>
  <section class="container_cards">
    <div class="card" v-for="item in paineis" :key="item.id">
      <h4>{{ item.titulo }}</h4>

      <strong class="value_vendas">R$ {{ item.valor }}</strong>
      <span :class="[box_status, item.status]">
        <i :class="item.iconPorcen"></i>
        {{ item.porcentagemVenda }}%
      </span>
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  name: "PaineisVendas",
  data() {
    return {
      paineis: [],
      box_status: "box_porcen",
    };
  },
  methods: {
    async getCardPaineis() {
      try {
        const dataFetch = await axios("http://localhost:3000/Paineis_Vendas");

        this.paineis = dataFetch.data.Paineis;
      } catch (ERROR) {
        console.error("Erro ao buscar dados de Paineis: ", ERROR);
      }
    },
  },

  mounted() {
    this.getCardPaineis();
  },
};
</script>

<style scoped>
.container_cards {
  min-width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 2rem;
  margin-top: 2rem;
}

.card {
  height: 13rem;
  width: 25%;
  border-radius: 1rem;
  background: var(--white);
  box-shadow: 0 1rem 1.2rem rgba(0, 0, 0, 0.1);
  padding: 2rem;
}

.card h4 {
  font-family: var(--main-font);
  font-size: 1.6rem;
  color: var(--dark);
  font-style: normal;
}

.card .value_vendas {
  display: block;
  color: #272727;
  font-size: 2.2rem;
  font-family: var(--main-font);
  margin-top: 1rem;
  margin-bottom: 1.5rem;
}

.box_porcen {
  padding: 0.5rem 1rem;
  border-radius: 2rem;
  font-size: 1.5rem;
  font-family: var(--main-font);
}

.positivo {
  background: #0bb07b0f;
  color: var(--success);
}

.negativo {
  background: #f03d3d0f;
  color: var(--error);
}
</style>