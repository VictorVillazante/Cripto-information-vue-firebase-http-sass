<template>
    <div>
        <form @submit.prevent="obtener">
            <div>
                <label>
                    Moneda nacional
                </label>
                <select name="" id="" required v-model="moneda">
                    <option selected>BOL</option>
                    <option>USD</option>
                    <option>EUR</option>
                </select>
            </div>
            <div>
                <label>
                    Criptomoneda
                </label>
                <select name="" id="" required v-model="cripto">
                    <option selected>BTC</option>
                    <option>ETH</option>
                    <option>LTC</option>
                </select>
            </div>
            <div>
                <button type="submit">Cotizar</button>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    data:()=>({
        moneda:"",
        cripto:""
    }),
    methods:{
        async obtener(){
            console.log(this.moneda+" "+this.cripto);
            const resp=await fetch("https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC&tsyms=USD,EUR");
            const data=await resp.json();
            console.log(data);
        }
    }
}
</script>

<style>

</style>