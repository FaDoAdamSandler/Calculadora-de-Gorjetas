<script>
export default {
  data() {
    return {
      quals: [
        { qual: 5, servico: "5% (Péssimo)" },
        { qual: 10, servico: "10% (Ruim)" },
        { qual: 15, servico: "15% (OK)" },
        { qual: 20, servico: "20% (Bom)" },
        { qual: 25, servico: "25% (Mais que bom)" },
        { qual: 30, servico: "30% (Excepcional)" },
      ],
      valor: 0,
      pessoa: 1,
      qual_selecionada: "",
    };
  },
  computed: {
    valor_final() {
      return (
        (this.valor * (1 + this.qual_selecionada / 100)) /
        this.pessoa
      ).toFixed(2);
    },
  },
};
</script>
<template>
  <main>
    <div class="calc">
      <h1>Calculadora de Gorjetas</h1>
      <div class="valores-forms">
        <label for="input-valor">Qual o valor da conta?</label>
        <input v-model="valor" placeholder="0" id="input-valor" type="number" />
      </div>
      <div class="valores-forms">
        <label for="select-servico">Como foi o serviço?</label>
        <select
          v-model="qual_selecionada"
          name="select-qual"
          id="select-servico"
        >
          <option disabled value="">Escolha um item</option>
          <option
            v-for="qual of quals"
            :key="qual.qual"
            for="select-servico"
            :value="qual.qual"
          >
            {{ qual.servico }}
          </option>
        </select>
      </div>
      <div class="valores-forms">
        <label for="input-pessoas"
          >Quantas pessoas estão pagando a conta?</label
        >
        <input
          v-model="pessoa"
          placeholder="1"
          id="input-pessoas"
          type="number"
        />
      </div>
    </div>
    <div class="resultado">
      <h2>Valor da conta:</h2>
      <span>R$ {{ valor_final }} por pessoa</span>
    </div>
  </main>
</template>
