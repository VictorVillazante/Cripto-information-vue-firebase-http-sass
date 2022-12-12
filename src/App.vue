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
  <reload-prompt/>
</template>

<script>
import Formulario from './components/Formulario.vue';
import Data from './components/Data.vue';
import Grid from './components/Grid.vue';
import ReloadPrompt from './components/ReloadPrompt.vue';
export default {
    components: { Formulario, Data, Grid,ReloadPrompt },
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
            const {RAW}=await resp.json();
            const dataCripto=RAW[cripto];
            const data=dataCripto[moneda];
            console.log(data);
            this.info.cripto=cripto;
            this.info.moneda=moneda;
            this.info.img=data.IMAGEURL;
            this.info.precio=data.PRICE;
        }

    }
}
</script>

<style>

</style>