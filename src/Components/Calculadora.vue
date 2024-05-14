<script setup>
import { reactive } from 'vue';

const estado = reactive({
    n1: '',
    n2: '',
    operacoes: {
        soma: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => (b !== 0 ? a / b : 'Divisão por zero'),
    },
    r: 0,
});

const res = () => {
    const { n1, n2, operacaoMatematica } = estado;
    estado.r = estado.operacoes[operacaoMatematica](parseFloat(n1), parseFloat(n2));
};
</script>

<template>
    <div class="container ">
        <h1 class="titulo">Calculadora</h1>
        <div class="numeros">
            <input type="text" v-model="estado.n1" @input="res" />
            <input type="text" v-model="estado.n2" @input="res" />

            <select v-model="estado.operacaoMatematica" @change="res">
                <option value="soma">Soma</option>
                <option value="subtracao">Subtração</option>
                <option value="multiplicacao">Multiplicação</option>
                <option value="divisao">Divisão</option>
            </select>

            <p>Resultado: {{ estado.r }}</p>

        </div>
    </div>
</template>

<style scoped>
.container {
    max-width: 700px;
    margin: 0 auto;
    margin-top: 120px;
    padding: 20px;
}

.titulo {
    font-size: 2em;
    text-align: center;
}

input {
    margin: auto;
    margin-top: 15px;
    margin-left: 15px;
    margin-right: 15px;
    padding: 8px;
    width: 300px;
    border: 1px solid #ccc;
    border-radius: 3px;
    display: inline;
    align-items: center;
    text-align: center;

}

select {
    margin: auto;
    margin-top: 15px;
    padding: 8px;
    width: 150px;
    border: 1px solid #ccc;
    border-radius: 3px;
    display: flex;
    align-items: center;
    text-align: center;
}

p{
    max-width: 130px;
    margin: 0 auto;
    margin-top: 15px;
    font-size: 1.5em;
}
</style>