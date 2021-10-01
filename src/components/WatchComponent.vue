<template>
  <div>
    <h1> Elo mordo </h1>
    <p>Masz <strong> {{shares}} </strong> akcji o wartości <strong> {{sharesValue}}</strong>. Cena pojedynczej akcji wynosi <strong> {{sharePrice}} </strong></p> <br>
    <p v-if="shares<0" style="color: red">Ilość akcji nie może być mniejsza od 0!</p>
    <button @click="changeNumberOfShares(1)">Kup 1 akcję</button>
    <button @click="changeNumberOfShares(5)">Kup 5 akcji</button>
    <button @click="changeNumberOfShares(-1)">Sprzedaj 1 akcję</button>
    <button @click="changeNumberOfShares(-5)">Sprzedaj 5 akcji</button>

 
  </div>
</template>

<script>
import { computed, ref, watch } from 'vue'
export default {
  name: "WatchComponent",
  setup() {
    const shares = ref(15);
    const sharePrice = ref(10);
    const sharesValue = computed(() => shares.value * sharePrice.value);
  
  function changeNumberOfShares(number) {
        if (shares.value + number>=0) {
          shares.value +=number
        }
  }
//co chcemy obserwować? watch([co ma się zmieniać, co ma się zadziać], [inna rzecz co się zmienia, co się dzieje po zmianie])
  watch(shares,  (shares, prevShares)=> {
    shares> prevShares ? getPrice(1,5) : getPrice (-5, -1)
  })
  // watch(shares, ()=> {console.log("ilość akcji smieniła się")})

  function getPrice (min, max) {
    const priceDiff = Math.floor(Math.random()* (max-min)+min)
    if (sharePrice.value + priceDiff >=0)     
    sharePrice.value +=priceDiff
  }

  return {shares, sharePrice, sharesValue, changeNumberOfShares}
  }
}
</script>