<template>
  <div id="app">
    <BankManagement/>
    <MortgageCalculator/>
  </div>
</template>

<script>
import BankManagement from '@/components/BankManagement'
import MortgageCalculator from '@/components/MortgageCalculator'

export default {
  name: 'App',
  components: {
    BankManagement,
    MortgageCalculator
  }
}
</script>
