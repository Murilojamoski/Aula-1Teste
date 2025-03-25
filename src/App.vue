<script setup>
import { ref } from "vue";
const valor = ref(10)
let click =  ref(1)
let custo = ref(10)
let auto = ref(false)


function autaDes(){
  if(valor.value >= 100){
    valor.value -= 100
     auto.value = true
     console.log(auto.value)
  }
  if(auto.value == true){
  setInterval(()=>{
    valor.value += 3
    console.log("+3")
  }, 1000)
}
 
}

  

function incrementar(){
  valor.value += click.value
}

function tirar(){
  valor.value -= click.value
}

function upgrade(){
  if (valor.value >= custo.value && click.value < 2){
    click.value += 1
    valor.value -= 10
    custo.value = 100
    return
  }
  if(custo.value >= 100 && custo.value <= 999){
      click.value += 10
      valor.value -= 100
      if(click.value >= 50){
        custo.value = 1000
      }
  }
  if(valor.value >= custo.value){
    click.value += 100
    valor.value -= 1000
  }

}
console.log(valor)
</script>

<template>
  <div>
  <h1>{{ valor }}</h1>
  <button @click="incrementar()">incrementar</button>
  <button @click="tirar()">descrementar</button>
  <button @click="upgrade()">upgrade (custo {{ custo }})</button>
  <button @click="autaDes()">autoCliker (custo 100)</button>
  <p>valor do clique: {{ click }}</p>

  </div>
</template>

<style scoped>
  button{
    margin: 1vw;
    padding: 5px;
    border-radius: 10px;
    border: none;
  }
  div{
    text-align: center;
  }
</style>
