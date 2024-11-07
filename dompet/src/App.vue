<template>
  <div class="container">
    <h2 class="title">Dompetku – Expense & Income Management</h2>
    
    <!-- Input Form -->
    <div class="input-form">
      <input
        v-model="description"
        type="text"
        placeholder="Description"
        class="input-field"
      />
      <input
        v-model.number="amount"
        type="number"
        placeholder="Amount"
        class="input-field"
      />
      <button @click="addTransaction" class="submit-btn">Add Transaction</button>
    </div>

    <!-- List of Transactions -->
    <ul class="transaction-list">
      <li v-for="(transaction, index) in transactions" :key="index" class="transaction-item">
        <span>{{ transaction.description }} - ${{ transaction.amount.toFixed(2) }}</span>
        <button @click="removeTransaction(index)" class="delete-btn">Delete</button>
      </li>
    </ul>

    <!-- Button to Clear All Transactions -->
    <button @click="clearAll" class="clear-all-btn">Clear All</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      description: "",
      amount: null,
      transactions: [],
    };
  },
  methods: {
    addTransaction() {
      if (this.description && this.amount) {
        // Add new transaction to the list
        this.transactions.push({
          description: this.description,
          amount: this.amount,
        });
        // Clear input fields
        this.description = "";
        this.amount = null;
      }
    },
    removeTransaction(index) {
      this.transactions.splice(index, 1); // Remove specific transaction
    },
    clearAll() {
      this.transactions = []; // Clear all transactions
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: auto;
  text-align: center;
  font-family: 'Roboto', sans-serif;
  background-color: #fafafa;
  border-radius: 8px;
  padding: 2em;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.title {
  color: #3a3a3a;
  font-size: 2.5em;
  margin-bottom: 1em;
}

.input-form {
  margin-bottom: 2em;
}

.input-field {
  width: 40%;
  padding: 0.8em;
  margin: 0.5em;
  border-radius: 5px;
  border: 1px solid #ccc;
  font-size: 1em;
  transition: border-color 0.3s;
}

.input-field:focus {
  border-color: #ff6f61;
  outline: none;
}

.submit-btn {
  padding: 0.8em 2em;
  background-color: #28a745;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 1.1em;
  cursor: pointer;
  transition: background-color 0.3s;
}

.submit-btn:hover {
  background-color: #218838;
}

.transaction-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.transaction-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0.8em 0;
  padding: 1em;
  background-color: #f0f8ff;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.transaction-item span {
  font-size: 1.2em;
  color: #3a3a3a;
}

.delete-btn {
  background-color: #ff4d4d;
  color: white;
  padding: 0.5em 1em;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1em;
  transition: background-color 0.3s;
}

.delete-btn:hover {
  background-color: #e43f3f;
}

.clear-all-btn {
  margin-top: 1.5em;
  background-color: #f8c102;
  color: white;
  padding: 0.8em 2em;
  border: none;
  border-radius: 5px;
  font-size: 1.1em;
  cursor: pointer;
  transition: background-color 0.3s;
}

.clear-all-btn:hover {
  background-color: #e6a300;
}
</style>