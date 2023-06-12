<script setup>
  import { reactive } from 'vue';
  import HeaderTitle from './components/HeaderTitle.vue';
  import CalcArea from './components/CalcArea.vue';

  const estado = reactive({
    erroCal: "Divisão por zero não permitida!",
    operacao: { operador: 'soma', operadorSimbol: '+'},
    numeros: { n1: "", n2: ""},

    imgCal: {
      multiplicacao: "*",
      divisao: "/",
      soma: "+",
      subtracao: "-"
    }
  });

  const opAtual = event => {
    const operacao = event.target.value;
    estado.operacao.operador = operacao;
    estado.operacao.operadorSimbol = estado.imgCal[operacao];
  }

  const definirOperador = () => {
    const tarefa = estado.operacao;
    return tarefa.operadorSimbol;
  };

  const pegarN1 = event => {
    const num1 = event.target.value;
    estado.numeros.n1 = num1;
  };

  const pegarN2 = event => {
    const num2 = event.target.value;
    estado.numeros.n2 = num2;
  };

  const calcular = () => {
    if (estado.numeros.n1 === "" && estado.numeros.n2 === "") {
      return "";
    } else if(estado.numeros.n1 >= 0 && estado.numeros.n2 == 0 && estado.operacao.operador == "divisao") {
      return "";
    } else {
      return eval(`${estado.numeros.n1} ${estado.operacao.operadorSimbol} ${estado.numeros.n2}`);
    }
  };

  const erroCalcular = () => {
    if (estado.operacao.operador === "divisao") {
      if (estado.numeros.n2 == 0) {
        return estado.erroCal;
      } else {
        return "";
      }  
    } else {
      return "";
    }
  }

  const atualizaPagina = () => {
    console.log("Página não atualizada!")
  }

</script>

<template>
  
  <div class="container">

    <HeaderTitle/>
    <CalcArea :pegarOperacao="opAtual" :definirOperador="definirOperador()" :numero1="pegarN1" :numero2="pegarN2" :calcular="calcular()" :erroCalcular="erroCalcular()" :updatePage="atualizaPagina"/>

  </div>

</template>
