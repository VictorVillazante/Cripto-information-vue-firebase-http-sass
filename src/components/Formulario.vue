<template>
    <div>
        <!-- <form @submit.prevent="obtener(cripto,moneda)"> -->
        <form @submit.prevent="$emit('infoMoneda',moneda,cripto)">
            <div>
                <label>
                    Moneda nacional
                </label>
                <select name="" id="" required v-model="moneda">
                    <option selected>MXN</option>
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
    // props:["obtener"]
   
}
</script>

<style>

</style>