<script setup></script>

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

      <button>⇄</button>

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

    <div class="body">
      <div class="main">
        <label for="amount">Amount</label>
        <input type="number" name="amount" />
      </div>
      <div class="main">
        <label for="result">Result</label>
        <input type="number" name="result" disabled />
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
  font-weight: bold;
  width: 3rem;
  height: 3rem;
  border: none;
  border-radius: 100%;
  background-color: rgb(18, 33, 202);
  color: white;
  cursor: pointer;
}

button:hover {
  background-color: rgb(48, 68, 185);
}
</style>
