<script setup>
import { ref, computed } from "vue";

const totalAmount = ref(0);
const numberOfPeople = ref(1);

const toPay = computed(() => {
  console.log(`totalAmonut.value = ${totalAmount.value}`);
  console.log(`numberOfPeople.value = ${numberOfPeople.value}`);

  if (totalAmount.value < 1 || numberOfPeople.value < 0) {
    return null;
  }

  return (totalAmount.value / numberOfPeople.value).toFixed(2);
});
</script>

<template>
  <main class="mx-auto container flex flex-col items-center">
    <h1 class="text-blue-800 my-10 text-2xl">
      Calculo de importe de pago por personas
    </h1>
    <div class="flex flex-col w-full px-60 justify-between">
      <label class="mr-10 my-2" for="totalAmount">Importe total</label>
      <input
        type="number"
        id="totalAmount"
        v-model="totalAmount"
        class="border p-2 w-full"
      />
    </div>
    <div class="flex flex-col w-full px-60 justify-content">
      <label class="mr-10 my-2 text-slate-500" for="numberOfPeople">Total personas</label>
      <input
        type="number"
        id="numberOfPeople"
        v-model="numberOfPeople"
        class="border p-2 w-full"
      />
    </div>

    <div class="flex flex-row items-center mt-10 text-xl text-orange-500" v-if="toPay">
      A pagar por persona <span class="ml-2 font-semibold text-3xl">$ {{ toPay }}</span>
    </div>
  </main>
</template>
