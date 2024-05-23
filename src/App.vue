<template>
  <div class="container">
    <h1 class="mt-5 mb-4">Calculadora</h1>
    <form>
      <div class="row">
        <div class="col-md-3">
          <input v-model="num1" type="number" class="mb-4 form-control" placeholder="1º Número">
        </div>
        <div class="col-md-3">
          <input v-model="num2" type="number" class="form-control" placeholder="2º Número">
        </div>
        <div class="col-md-5">
          <select v-model="operacaoSelecionada" @change="executarCalculo" class="form-control">
            <option value="" disabled selected>Escolha Uma Operação Aritmética</option>
            <option value="soma">Somar</option>
            <option value="subtracao">Subtrair</option>
            <option value="multiplicacao">Multiplicar</option>
            <option value="divisao">Dividir</option>
          </select>
        </div>
      </div>
    </form>
    <div class="mb-3">
      <br><span>Resultado: {{ resultado }}</span>
    </div>
  </div>
</template>

<script>

  export default{
    data(){
      return{
        operacaoSelecionada: '',
        resultado:    0,
        num1: 0,
        num2: 0
      }
    },

    watch:{
      num1(newVal,oldVal){
        this.executarCalculo()
      },
      num2(newVal,oldVal){
        this.executarCalculo()
      }
    },

    methods:{
      executarCalculo(){
        switch(this.operacaoSelecionada){
          case 'soma':
            this.resultado = this.num1 + this.num2
            break
          case 'subtracao':
            this.resultado = this.num1 - this.num2
            break
          case 'multiplicacao':
            this.resultado = this.num1 * this.num2
            break
          case 'divisao':
            this.resultado = this.num1 / this.num2
            break
        }
      }
    }
  }
</script>

<style scoped>
  .container{
    display: block;
    margin: 0 auto;
    align-items: center;
    width: 800px;
    background-color:rgb(241, 241, 241)
  }

  h1{
    text-align: center;
  }

  input{
    display: block;
    margin: 0 auto;
    text-align: center;
    width: 120px;
  }

  option{
    text-align: center
  }

  span{
    font-size: 20px;
  }

</style>

