


<script>
import Header from './components/Header.vue'
  import Balance from './components/Balance.vue'
  import IncomeExpense from './components/IncomeExpense.vue'
  import TransactionList from './components/TransactionList.vue'
  import AddTransaction from './components/AddTransaction.vue'
import {ref, computed} from 'vue'
export default {
  components: {Header, Balance, IncomeExpense, TransactionList, AddTransaction},
  setup(){
    const transaction = ref([
      {id:1, titel:"Food", value:-58.8},
      {id:2, titel:"Income", value:740},
      {id:3, titel:"Indomin", value:-40},
      {id:4, titel:"Soap", value:-80},
      {id:5, titel:"Fanta Drink", value:-35},
    ])

    const totalBalance = computed(()=>{
      return transaction.value.reduce((acc, item) => acc + item.value, 0)
    })

    const totalIncome = computed(()=>{
      return transaction.value.filter((item)=> item.value >0).reduce((acc,item)=> acc+item.value,0)
    })
    const totalExpense = computed(()=>{
      return transaction.value.filter((item)=> item.value <0).reduce((acc,item)=> acc+item.value,0)
    })
    const total = ref(5000)
    return {total , transaction,totalBalance, totalIncome,totalExpense}
  }
}

</script>

<template>
  <div>
    <Header/>
    <Balance :total="totalBalance"/>
    <IncomeExpense :income="totalIncome" :expense="totalExpense"/>
    <TransactionList :transaction="transaction"/>
    <AddTransaction/>
  </div>
</template>
