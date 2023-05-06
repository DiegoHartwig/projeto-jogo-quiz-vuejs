<template>
  <div>
    <h1>Jogo de Perguntas e Respostas, utilizando Vue Js</h1>

    <h2>Pergunta:</h2>

    <input type="radio" name="opcoes" value="true" />
    <label>Verdadeiro</label><br>

    <input type="radio" name="opcoes" value="false" />
    <label>Falso</label><br>

    <button class="salvar" type="button">Enviar</button>

  </div>
</template>

<script>

export default {
  name: 'App',
  components: {

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
