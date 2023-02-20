<script setup>
import { ref, computed } from "vue";

const fromCurrency = ref("USD");
const toCurrency = ref("EUR");
const amount = ref("");
const result = ref("");
const currencies = [
  "USD",
  "CHF",
  "EUR",
  "ALL",
  "MKD",
  "TRY",
  "GBP",
  "AED",
  "CNY",
  "INR",
  "JPY",
  "SAR",
  "RUB",
];
const exchangeRates = ref({});
const lastlyUpdated = ref();

fetch(
  `https://v6.exchangerate-api.com/v6/0714b1826cd73f6106ea6d5a/latest/${fromCurrency.value}`
)
  .then((response) => response.json())
  .then((data) => {
    lastlyUpdated.value = data.time_last_update_utc;
    exchangeRates.value = data.conversion_rates;
  });

const preventCharacters = () => {
  const validChars = /^[0-9+\-*/.]+$/;
  if (!validChars.test(amount.value)) {
    amount.value = amount.value.slice(0, -1);
  }
};

const changeSides = () => {
  const temp = fromCurrency.value;
  fromCurrency.value = toCurrency.value;
  toCurrency.value = temp;
};
</script>

<template>
  <section>
    <h1>Money Converter</h1>
    <h3>Easiest and simplest Currency Converter in the Internet</h3>
    <div class="body">
      <div class="main">
        <label>From</label>
        <select v-model="fromCurrency" id="from">
          <option v-for="currency in currencies" :value="currency">
            {{ currency }}
          </option>
        </select>
      </div>

      <button @click="changeSides" id="change-sides">⇄</button>

      <div class="main">
        <label>To</label>
        <select v-model="toCurrency" id="from">
          <option v-for="currency in currencies" :value="currency">
            {{ currency }}
          </option>
        </select>
      </div>
    </div>

    <div class="body">
      <div class="main">
        <label>Amount</label>
        <input type="number" v-model="amount" />
      </div>
      <div class="main">
        <label>Result</label>
        <input
          type="number"
          @input="preventCharacters"
          :value="
            (
              (amount * exchangeRates[toCurrency]) /
              exchangeRates[fromCurrency]
            ).toFixed(2)
          "
          readonly
        />
        <h2>{{ result }}</h2>
      </div>
    </div>
    <div>
      <h4>Lastly Updated: {{ lastlyUpdated }}</h4>
    </div>
  </section>
</template>

<style scoped>
section {
  margin: 0rem;
  padding: 3rem 19rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: rgb(108, 148, 242);
  border-radius: 8px;
}

h1 {
  font-size: 3rem;
}

h3 {
  text-align: center;
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
  margin: 0 1rem 1rem 1rem;
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

@media (max-width: 49rem) {
  h1 {
    font-size: 2rem;
  }

  section {
    margin: 0;
    padding: 1rem 0;
  }

  select,
  input {
    width: 7rem;
    height: 2.2rem;
  }

  button {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.4rem;
  }
}
</style>
