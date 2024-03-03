<script setup>
import { reactive } from 'vue';


const estado = reactive({
  valorA: 0,
  valorB: 0,
  filtro: 'Somar',
  tarefas: [
    {
      titulo: 'Somar',
      finalizada: true,
    },
    {
      titulo: 'Subtrair',
      finalizada: false,
    },
    {
      titulo: 'Multiplicar',
      finalizada: false,
    },
    {
      titulo: 'Dividir',
      finalizada: false,
    }


  ]
})

function tarefaSomar() {
  const { valorA, valorB } = estado;
  return parseInt(valorA) + parseInt(valorB);
}
function tarefaSubtrair() {
  const { valorA, valorB } = estado;
  return parseInt(valorA) - parseInt(valorB);
}
function tarefaMultiplicar() {
  const { valorA, valorB } = estado;
  return parseInt(valorA) * parseInt(valorB);
}
function tarefaDividir() {
  const { valorA, valorB } = estado;
  return parseInt(valorA) / parseInt(valorB);
}

const getOperadores = () => {
  const { filtro } = estado;

  switch (filtro) {
    case 'Somar':
      return tarefaSomar();
    case 'Subtrair':
      return tarefaSubtrair();
    case 'Multiplicar':
      return tarefaMultiplicar();
    case 'Dividir':
      return tarefaDividir();
    default:
      return estado.tarefas
  }

}

</script>

<template>
  <div class="container">
    <header class="mb-3 mt-5 bg-secondary rounded-3 text-white d-flex justify-content-center">
      <h1>Calculadora Aritimética</h1>
    </header>
    <form>
      <div class="row">
        <div class="col">
          <input @keyup="evento => estado.valorA = evento.target.value" type="number" placeholder="Digite aqui o Valor A"
            class="form-control" id="valorA">
        </div>
        <select @change="evento => estado.filtro = evento.target.value" class="col-md-2 rounded-3">
          <option value="+">Somar</option>
          <option value="-">Subtrair</option>
          <option value="*">Multiplicar</option>
          <option value="/">Dividir</option>

        </select>
        <div class="col">
          <input @keyup="evento => estado.valorB = evento.target.value" type="number" placeholder="Digite aqui o Valor B"
            class="form-control" id="valorB">
        </div>

        <div class="row d-flex justify-content-center">
          <div class="col-md-3">
            <h3 class="bg-light mt-3 border border-secondary rounded-3">{{ getOperadores () }}</h3>
            
          </div>
        </div>

      </div>
    </form>

  </div>
</template>

<style scoped></style>
