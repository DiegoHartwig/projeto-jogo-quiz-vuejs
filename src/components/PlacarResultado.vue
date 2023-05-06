<template>
    <section class="placar">
        Jogador<span>{{ this.pontosJogador }}</span> X
        <span>{{ this.pontosComputador }}</span> Computador
    </section>
</template>

<script>
export default {
    props:['pontosJogador', 'pontosComputador']
}

</script>

<style lang="scss">
section.placar {
    border-bottom: 1px solid black;
    padding: 24px;
    font-size: 20px;

    span {
        padding: 10px;
        font-weight: bold;
        border: 1px solid black;
    }
}
</style>