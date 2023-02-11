<script setup></script>

<template>
  <section>
    <h1>Money Converter</h1>
    <h3>Easiest and simplest Money Converter in Internet</h3>
    <div>
      <label for="from"></label>
      <select name="from" id="from">
        <option value="Franc">CHF - Swiss Franc</option>
        <option value="Euro">EUR - Euro</option>
        <option value="Dollar">USD - Dollar</option>
        <option value="Pound">GBP - British Pound</option>
      </select>
    </div>

    <button>Change sides</button>

    <div>
      <select name="to" id="to">
        <option value="Franc">CHF - Swiss Franc</option>
        <option value="Euro">EUR - Euro</option>
        <option value="Dollar">USD - Dollar</option>
        <option value="Pound">GBP - British Pound</option>
      </select>
    </div>

    <label for="amount">Amount</label>
    <input type="number" name="amount" />

    <h2>Result: (result)</h2>
  </section>
</template>
