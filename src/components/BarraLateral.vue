<template>
    <header>
        <div class="container">
            <img src="../assets/biaTracker.png" alt="Logotipo Bia Tracker">
            <p>Bia Tracker</p>
        </div>
        <button class="button" @click="alterarTema">
            {{textoBotao}}
        </button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data () {
        return {
            modoEscuroAtivo: false
        }
    },
    computed: {
        textoBotao () {
            if (this.modoEscuroAtivo) {
                return 'Desativar modo escuro';
            }
            return 'Ativar modo escuro';
        }
    },
    methods: {
        alterarTema() {
            // Altera o valor da variável modoEscuroAtivo por meio do operador de negação lógica (!)
            this.modoEscuroAtivo = !this.modoEscuroAtivo;
            // Emite o evento aoTemaAlterado com o valor atual da variável modoEscuroAtivo
            this.$emit('aoTemaAlterado', this.modoEscuroAtivo);
            
        }
    }
});

</script>

<style scoped>
header {
    padding: 2rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;

}
.button {
    margin: 3rem;
}

.container {
    display: flex;
    justify-content: center;
    align-items: center;/* Opcional, alinha no eixo vertical */
    gap: 20px;/* Espaçamento entre os elementos */
    color: white;
}

img {
    width: 150px;
}

p {
    font-size: 24px;
}
@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>