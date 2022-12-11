<template>
  <div class="container">
    <h1>Cripto Compiler</h1>
    <hr>  
    <Grid>
      <!-- <Formulario :obtener="obtener"/> -->
      <Formulario @info-moneda="obtener"/>
      <Data :cripto="info.cripto" :moneda="info.moneda" :img="info.img" :precio="info.precio"/>
    </Grid>
  </div>
 

</template>

<script>
import Formulario from './components/Formulario.vue';
import Data from './components/Data.vue';
import Grid from './components/Grid.vue';
export default {
    components: { Formulario, Data, Grid },
    data:()=>({
      info:{
        cripto:"*",
        moneda:"*",
        img:"",
        precio:"0"
      }
    }),
    methods:{
        async obtener(cripto,moneda){
            console.log(moneda+" "+cripto);
            //const resp=await fetch(`https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC&tsyms=USD,EUR`);
            const resp=await fetch(`https://min-api.cryptocompare.com/data/pricemultifull?fsyms=${cripto}&tsyms=${moneda},`);

            const data=await resp.json();
            console.log(data);
            const dataCripto=data.RAW[cripto];
            const dataMoneda=dataCripto[moneda];
            console.log(dataMoneda);
        }
    }
}
</script>

<style>

</style>