<script setup>
import { SourceMapGenerator } from 'source-map';
import { reactive } from 'vue';


const estado = reactive ({
  operador : 'somar',
  num2 :'',
  num1 : '',
  resultado: '',
  
})
    function dividir(num1,num2) {
      return num1 / num2;
    }
    function multiplicar(num1,num2) {
      return num1 * num2;
    }
    function subtrair(num1,num2) {
      return num1 - num2;
    }
    function somar(num1,num2) {
    return num1 + num2;
    }

const funcaoCalculadora = () => {
  const {operador} = estado;
  const {num1} = estado;
  const {num2} = estado;
  switch (operador) {
    case 'somar':
      return estado.resultado = somar(num1,num2);
    case 'subtrair':
      return estado.resultado = subtrair(num1,num2);
    case 'multiplicar':
      return estado.resultado = multiplicar(num1,num2);
    case 'dividir':
      return estado.resultado = dividir(num1,num2);
  }
}


</script>

<template>
  <div class="container">
    <h1>Calculadora</h1>
    
    <form>
      
      <input type="number" v-model="estado.num1" placeholder="Digite um número"/>
      <select @change="evento => estado.operador = evento.target.value" class="form-control" >
        <option value="somar">+</option>
        <option value="subtrair">-</option>
        <option value="multiplicar">X</option>
        <option value="dividir">÷</option>
      </select>
      <input type="number" v-model="estado.num2" placeholder="Digite um número"/>
    </form>
    <span>Resultado = {{funcaoCalculadora()}}</span>
      <h2 class="resultado"></h2>
  </div>
</template>

<style scoped>

.container{
  margin:0 auto;
  max-width: 400px;
  height: 400px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: blanchedalmond;
  font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  border-radius: 20px;
}
h1{
  color: rgb(111, 114, 117);

}

span{
  font-size: 24px;
  margin-top: 20px;
}
input{
  background-color: #eee;
  max-width: 100px;
  border-radius: 3px;
  border: transparent;
  text-align: center;
  font-size: 24px;
}
select{
  font-size: 24px;
  width: 45px;
  height: 30px;
  background-color: #f19f9f;
  border-radius: 3px;
  margin: 0 15px;
}
</style>
