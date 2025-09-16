<script lang="ts">
export default {
  data() {
    return {
      caixaAberta: -1,
      caixas: [{ nome: "caixa1", mensagem: "Surpresa! 🎁" },
      { nome: "caixa2", mensagem: "Você desbloqueou o segredo! 🔑" },
      { nome: "caixa3", mensagem: "Mensagem secreta revelada! ✨" }]
    }
  },
  methods: {
    botaoDesbloqueado(index: number) {
      this.caixaAberta = this.caixaAberta === index ? -1 : index;
    }
  }
}
</script>

<template>
  <ul class="corpo__botao">
    <li v-for="(item,index) in caixas" :key="index">
      <button class="botaoNaTela" @click="botaoDesbloqueado(index)">Clique aqui para ver o segredo</button>
      <div v-if="caixaAberta === index">
        {{ item.mensagem }}
      </div>
     
    </li>
  </ul>
</template>

<style scoped>
.corpo__botao {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem; /* espaço entre as caixas */
  margin-top: 2rem;
  padding: 0;
}

.corpo__botao li {
  list-style: none; /* tira as bolinhas do li */
  text-align: center;
}

.botaoNaTela {
  padding: 0.8rem 1.5rem;
  font-size: 1rem;
  font-weight: bold;
  background: linear-gradient(90deg, #f5a623, #f76b1c);
  color: white;
  border: none;
  border-radius: 0.8rem;
  cursor: pointer;
  transition: transform 0.2s, box-shadow 0.2s;
}

.botaoNaTela:hover {
  transform: scale(1.05);
  box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.3);
}

.corpo__botao div {
  margin-top: 0.8rem;
  padding: 0.8rem 1rem;
  background-color: #fdf6e3;
  border-radius: 0.5rem;
  font-size: 1rem;
  font-weight: 500;
  color: #333;
  box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}</style>