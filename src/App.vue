<template>
  <template v-if="this.pergunta">

    <h1 v-html="this.pergunta"></h1>

    <template v-for="(resposta, index) in this.respostas" :key="index">
      <input :disabled="this.respostaEnviada" type="radio" name="opcoes" :value="resposta"
        v-model="this.respostaSelecionada" />
      <label v-html="resposta"></label><br>
    </template>

    <button v-if="!this.respostaEnviada" @click="this.enviarResposta" class="salvar" type="button">Enviar</button>

    <section v-if="this.respostaEnviada" class="result">
      <h4 v-if="this.respostaCorreta == this.respostaSelecionada">&#9989; Parabéns! A resposta {{ this.respostaCorreta
      }} está correta!</h4>
      <h4 v-else>&#10060; Sinto muito, a resposta certa é {{ this.respostaCorreta }}.</h4>
      <button class="salvar" type="button">Próxima Pergunta </button>
    </section>

  </template>
</template>

<script>

export default {
  name: 'App',

  data() {
    return {
      pergunta: undefined,
      respostasIncorretas: undefined,
      respostaCorreta: undefined,
      respostaSelecionada: undefined,
      respostaEnviada: false
    }
  },

  computed: {
    respostas() {
      var respostas = JSON.parse(JSON.stringify(this.respostasIncorretas));
      respostas.splice(Math.round(Math.random() * respostas.length), 0, this.respostaCorreta);
      return respostas;
    }
  },

  methods: {
    enviarResposta() {
      if (!this.respostaSelecionada) {
        alert("Escolha uma resposta.");
      } else {
        this.respostaEnviada = true;
        if (this.respostaSelecionada == this.respostaCorreta) {
          console.log("Resposta correta;");
        } else {
          console.log("Resposta Incorreta.");
        }
      }
    }
  },

  created() {
    this.axios
      .get('https://opentdb.com/api.php?amount=1&category=18')
      .then((response) => {
        this.pergunta = response.data.results[0].question;
        this.respostaCorreta = response.data.results[0].correct_answer;
        this.respostasIncorretas = response.data.results[0].incorrect_answers;

        console.log(this.pergunta)
        console.log(this.respostaCorreta)
        console.log(this.respostaIncorreta)
      })
  }

}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  max-width: 960px;

  input[type=radio] {
    margin: 12px 4px;
  }

  button.salvar {
    margin-top: 12px;
    height: 40px;
    min-width: 120px;
    padding: 0 16px;
    color: #fff;
    background-color: #1868c0;
    border: 1px solid #1868c0;
    cursor: pointer;
    border-radius: 6px;
  }

}
</style>
