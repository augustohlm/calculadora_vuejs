<script setup>
import { reactive } from 'vue';


    const valores = reactive({
      numero1: 0,
      numero2: 0,
      operador: "+",
      resultado: 0,
    })

    function calculaOperacao() {
        const num1 = parseFloat(valores.numero1)
        const num2 = parseFloat(valores.numero2)

        switch(valores.operador){
          case '+':
            valores.resultado = num1+num2;
            break;
          
          case '-':
            valores.resultado = num1-num2;
            break;

          case '*':
            valores.resultado = num1*num2;
            break;

          case '/':
              if(num2 === 0){
              valores.resultado = "Informe um número diferente de 0";
            } else {
              valores.resultado = num1/num2;
            }
            break;

          default:
            valores.resultado;
        }

    }
</script>

<template>

    <div class="container">
        <div class="row">
            <div class="col">
                <header>
                    <h1 >Calculadora aritmética</h1>
                </header>
            </div>
            <form>
              <input @keyup="evento => {valores.numero1 = evento.target.value; calculaOperacao()}" type="number" placeholder="Insira um número">
              <select @change="evento => {valores.operador = evento.target.value; calculaOperacao()}">
                <option value="+">+</option>
                <option value="-">-</option>
                <option value="*">*</option>
                <option value="/">/</option>
              </select>
              <input @keyup="evento => {valores.numero2 = evento.target.value; calculaOperacao()}" type="number" placeholder="Insira um número">
              <h1 class="zero-p">=</h1>
              <div class="resultado">
                {{ valores.resultado }}
              </div>
            </form>
        </div>
    </div>

</template>

<style scoped>
  .container {
    margin: 200px auto;
    max-width: 900px;
    border-radius: 30px;
    background-color: #09020f;
    border: 3px solid  #7f7782;
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 1);
    color: #fcfcfc;
  }

  header{
  display: flex;
  padding: 50px;
  
}

.zero-p {
  margin: 0;
  padding-bottom: 7px;
}

  h1{
    margin: 0 auto;
    color: #fcfcfc;
  }

  form{
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 50px;
  background-color: #09020f;
  border-bottom-right-radius:30px ;
  border-bottom-left-radius:30px ;
}

select {
  margin: 0 4px;
}

.resultado {
  font-size: 20px;
  margin-left: 3px;
}

</style>
