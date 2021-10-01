<template>
  <div class="hello">
    <h1> Elo </h1>
    <p>
      <button @click="SagHallo">Sag Hallo</button> <br>
    </p>

    <!-- <h1>Price: {{ state.price }} </h1>
    <button @click="makeOrder">Make next order</button> <button @click="removeOneProduct">Remove one product</button>
    <br>
    <p>
      quantity: {{state.quantity}} <br>
      total price: {{ state.totalPrice }} <br>
      tax: {{state.tax}} <br>
    </p>
    <p v-if="state.tax>300">Morawiecki lubi to!</p> -->
    <!-- dla refastate. -->
    <h1>Price: {{ price }} </h1>
    <button @click="makeOrder">Make next order</button> <button @click="removeOneProduct">Remove one product</button>
    <br>
    <p>
      quantity: {{quantity}} <br>  
      total price: {{ totalPrice }} <br>
      tax: {{tax}} <br>
    </p>
<p v-if="tax>300">Morawiecki lubi to!</p>
  
  </div>
</template>

<script>
//używając 'ref'

// import { ref } from 'vue'
// export default {
//   name: "UseExternalAPI",
//   setup() {
//     const quantity = ref(0);
//     const price = ref(100)
//     const totalPrice = ref(0)
//     const tax = ref(0)

//     function makeOrder() {
//       quantity.value++
//       totalPrice.value = quantity.value * price.value
//       tax.value = totalPrice.value *0.23
//     }

//     function removeOneProduct () {
//       quantity.value--
//       totalPrice.value = quantity.value * price.value
//       tax.value = totalPrice.value *0.23
//     }

//    return { SagHallo, makeOrder, quantity, totalPrice, price,tax, removeOneProduct }

//uzywając 'reactive'
import { reactive, toRefs, computed } from 'vue'
export default {
  name: "UseExternalAPI",
  setup() {

    const state = reactive({
      quantity:0,
      price:89,
      totalPrice:computed(()=> state.price *state.quantity),
      tax: computed(()=> Math.round(state.totalPrice*0.23*100)/100)
    })

    function makeOrder() {
      state.quantity++
      // dzięki computed
      // state.totalPrice = state.quantity * state.price
      // state.tax= state.totalPrice *0.23
    }

    function removeOneProduct () {
      state.quantity--
      state.totalPrice = state.quantity * state.price
      state.tax = state.totalPrice *0.23
    }
    
    function SagHallo() {
      const wilkommenText = "No elo mordo";
      console.log(addExclamatioMark(wilkommenText));
    };

    function addExclamatioMark(text) {
        return `${text}!`;
    };
    return { SagHallo, makeOrder, removeOneProduct, ...toRefs(state) }
  }
};
</script>
