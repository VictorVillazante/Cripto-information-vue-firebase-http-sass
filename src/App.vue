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
            //console.log(data);
            this.info.cripto=cripto;
            this.info.moneda=moneda;
            this.info.img=`https://www.cryptocompare.com${data.IMAGEURL}`;
            if(moneda=="BTC"){
              this.info.img="https://img.freepik.com/vector-gratis/fondo-moneda-oro-bitcoin-criptomoneda_1017-31505.jpg?w=2000";
            }
            if(moneda=="ETH"){
              this.info.img="https://img.freepik.com/free-psd/3d-etherium-nft-cryptocurrency-graphic-chart_393336-343.jpg?w=826&t=st=1694876513~exp=1694877113~hmac=3b31228bdb0cec692533656ce64e35c1bc7aaa6f177f01a7b6e8f18ba5b2b7d2";
            }
            if(moneda=="LTC"){
              this.info.img="https://img.freepik.com/free-photo/coins-litecoin-against-background-australia-australian-flag-close-up_169016-6296.jpg?w=1380&t=st=1694876551~exp=1694877151~hmac=8cf122df652558bd193d9e4dd4d8cdb9595b0455d7c7360db74ac663fc1b572e";
            }       
            console.log(this.info.img);
            this.info.precio=data.PRICE;
        }

    }
}
</script>

<style>

</style>