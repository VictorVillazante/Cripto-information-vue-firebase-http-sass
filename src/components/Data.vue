<template>
  <div class="data">
    <h2>Informacion</h2>
    <h3><span class="cripto">{{cripto}}</span>--<span class="moneda">{{moneda}}</span></h3>
    <div>
      <img :src="`https://www.cryptocompare.com${img}`" alt="">
      <p>
        Precio: <strong>${{precio}}</strong>
      </p>      
    </div>
  </div>
  
</template>

<script>
export default {
  props:{
    cripto:{
      type:String,
      required:true
    },
    moneda:{
      type:String,
      required:true
    },
    img:{
      type:String,
      required:true
    },
    precio:{
      type:String,
      required:true
    }
  }
}
</script>

<style>

</style>