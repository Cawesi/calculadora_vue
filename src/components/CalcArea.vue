<script setup>
    const props = defineProps(['pegarOperacao', 'definirOperador', 'numero1', 'numero2', 'calcular', 'erroCalcular', 'updatePage']);
</script>

<template>
    <div class="row mt-4">
      <form class="form-control text-center py-4"  @submit.prevent="props.updatePage">
        <input type="number" required class="me-2" placeholder="Insira o valor" @change="props.numero1">
        <span class="me-2">{{props.definirOperador}}</span>
        <input type="number" required class="me-4" placeholder="Insira o valor" @change="props.numero2">  
        
        <select @change="props.pegarOperacao">
          <option value="soma">Soma</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>

        <div class="row mt-3 d-flex justify-content-center">
            <span class="w-25 py-1 bg-warning border border-warning-subtle rounded">
                <i class="bi bi-arrow-right"></i> {{ props.calcular }}
            </span>
        </div>

        <div class="row d-flex justify-content-center">
            <span class="w-25 py-1 text-danger">
                <small>
                    {{ props.erroCalcular }}
                </small>
            </span>
        </div>
      </form>
    </div>
</template>