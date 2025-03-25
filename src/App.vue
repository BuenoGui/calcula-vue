<script setup>
  import { reactive } from 'vue';

  const estado = reactive ({
    a: 0,
    b: 0,

    operacao: 'Somar',
    resultado: 0
  })

const contas = {
  Somar: (a,b) => a + b,
  Subtrair: (a,b) => a - b,
  Dividir: (a,b) => a / b,
  Multiplicar: (a,b) => a * b,
  Porcentagem: (a,b) => (a * b) / 100
}

function calcular() {
  const {a, b, operacao } = estado;
  const NumeroA = Number(a);
  const NumeroB = Number(b);

  estado.resultado = contas[operacao]?.(NumeroA, NumeroB) || 'Azedou o caldo do leite'
}

</script>

<template>
  <section>
    <div class="container d-flex flex-column">

      <div class="container-header d-flex justify-content-center">
        <input type="number" v-model="estado.a" @change="calcular">
        <select v-model="estado.operacao" @change="calcular">
          <option value="Somar">+</option>
          <option value="Subtrair">-</option>
          <option value="Dividir">/</option>
          <option value="Porcentagem">%</option>
          <option value="Multiplicar">x</option>
        </select>
        <input type="number"  v-model="estado.b" @change="calcular">
      </div>

      <div class="col text-center">
        <div class="container">
          <p class="m-0">Resultado:</p>
          <textarea :value="estado.resultado" class="text-center" readonly> 157 </textarea>
        </div>
      </div>

      </div>

      <div class="container col-12">


    </div>
  </section>
</template>

<style scoped>
    section {
      height: 100vh;
      width: 100vh;
      display: flex;
      align-items: center;
    }
</style>
