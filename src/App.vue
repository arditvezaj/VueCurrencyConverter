<script setup>
import { ref } from "vue";

const amount = ref();
const result = ref();
const fromCurrency = ref("USD");
const toCurrency = ref("EUR");
const currencies = ["USD", "CHF", "EUR", "GBP"];

const exchangeRates = {
  USD: 1,
  EUR: 0.86,
  GBP: 0.76,
  CHF: 0.93,
};

const convert = () => {
  result.value = (
    (amount.value * exchangeRates[toCurrency.value]) /
    exchangeRates[fromCurrency.value]
  ).toFixed(2);
};
</script>

<template>
  <section>
    <h1>Money Converter</h1>
    <h3>Easiest and simplest Money Converter in Internet</h3>
    <div class="body">
      <div class="main">
        <label>From</label>
        <select v-model="fromCurrency" id="from">
          <option v-for="currency in currencies" :value="currency">
            {{ currency }}
          </option>
        </select>
      </div>

      <button id="change-sides">⇄</button>

      <div class="main">
        <label>To</label>
        <select v-model="toCurrency" id="from">
          <option v-for="currency in currencies" :value="currency">
            {{ currency }}
          </option>
        </select>
      </div>
    </div>

    <button @click="convert" id="convert">Convert</button>

    <div class="body">
      <div class="main">
        <label>Amount</label>
        <input type="number" v-model="amount" />
      </div>
      <div class="main">
        <label>Result</label>
        <input type="number" v-model="result" readonly />
      </div>
    </div>
  </section>
</template>

<style scoped>
section {
  margin: 4rem 25%;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgb(108, 148, 242);
  border-radius: 8px;
}

h1 {
  font-size: 3rem;
}

.body {
  display: flex;
  align-items: center;
}

.main {
  margin: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}

select,
input {
  margin-bottom: 1rem;
  width: 12rem;
  height: 3rem;
  border-radius: 5px;
  border: 1px solid black;
  text-align: center;
}

select,
input,
label {
  font-size: 1.2rem;
}

button {
  margin-top: 1rem;
  font-size: 1.8rem;
  border: none;
  background-color: rgb(18, 33, 202);
  color: white;
  cursor: pointer;
}
button:hover {
  background-color: rgb(48, 68, 185);
}

#change-sides {
  width: 3rem;
  height: 3rem;
  border-radius: 100%;
}

#convert {
  padding: 0.5rem 1rem;
  border-radius: 8px;
}
</style>
