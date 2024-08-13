<template>
  <div class="atm">
    <h2>Welcome to the ATM Machine</h2>
    <button @click="checkBalance">Check Balance</button>
    <button @click="withdraw">Withdraw</button>
    <input type="number" v-model.number="amount" placeholder="Enter Amount" min="1">
    <div id="output">{{ output }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      balance: 1000,
      amount: null,
      output: ''
    };
  },
  methods: {
    checkBalance() {
      this.output = `Your current balance is $${this.balance}`;
    },
    withdraw() {
      if (isNaN(this.amount) || this.amount <= 0) {
        this.output = "Please enter a valid amount.";
      } else if (this.amount > this.balance) {
        this.output = "Insufficient funds.";
      } else {
        this.balance -= this.amount;
        this.output = `You have withdrawn $${this.amount}. Your current balance is $${this.balance}`;
        this.amount = null; // Reset the input field
      }
    }
  }
};
</script>

<style>
body {
  background-color: #e3e3e3;
  font-family: Roboto, sans-serif;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.atm {
  background-color: #333;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
  text-align: center;
  width: 300px;
  color: #fff;
}

h2 {
  margin-top: 0;
  color: #ffd700;
  margin-bottom: 20px;
}

button {
  margin-top: 10px;
  padding: 10px 20px;
  background-color: #ffd700;
  color: #333;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #ffec8b;
}

input[type="number"] {
  width: 100px;
  padding: 8px;
  margin-top: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
}

#output {
  background-color: #ffd700;
  color: #333;
  border-radius: 5px;
  padding: 10px;
  margin-top: 10px;
}
</style>
