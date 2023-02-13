<script setup>
import { ref } from "vue";

const amount = ref(0);
const result = ref(0);
const from = ref("CHF - Swiss Franc");
const to = ref("EUR - Euro");

const exchangeRates = {
  dollar: 1,
  eur: 0.86,
  pound: 0.76,
};

const convert = () => {
  result.value = amount.value * exchangeRates.eur;
};
</script>

<template>
  <section>
    <h1>Money Converter</h1>
    <h3>Easiest and simplest Money Converter in Internet</h3>
    <div class="body">
      <div class="main">
        <label for="from">From</label>
        <select name="from" id="from">
          <option value="franc">CHF - Swiss Franc</option>
          <option value="euro">EUR - Euro</option>
          <option value="dollar">USD - Dollar</option>
          <option value="pound">GBP - British Pound</option>
        </select>
      </div>

      <button id="change-sides">⇄</button>

      <div class="main">
        <label for="to">To</label>
        <select name="to" id="to">
          <option value="franc">CHF - Swiss Franc</option>
          <option value="euro">EUR - Euro</option>
          <option value="dollar">USD - Dollar</option>
          <option value="pound">GBP - British Pound</option>
        </select>
      </div>
    </div>

    <button @click="convert" id="convert">Convert</button>

    <div class="body">
      <div class="main">
        <label for="amount">Amount</label>
        <input type="number" name="amount" v-model="amount" />
      </div>
      <div class="main">
        <label for="result">Result</label>
        <input type="number" name="result" v-model="result" />
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
