<template>
  <BContainer>
    <bank-table :banks="banks" @remove="remove($event)" @update="edit($event)"/>
    <BModal v-model="modalShow" lazy hide-footer hide-header>
      <bank-update :bank="updating" @input="update($event)" @cancel="cancelEdit()"/>
    </BModal>
  </BContainer>
</template>

<script>
import BankTable from '@/components/BankTable'
import BankUpdate from '@/components/BankUpdate'
import Footer from '@/components/Footer'
import Header from '@/components/Header'

export default {
  name: 'BankManagement',
  components: { BankTable, BankUpdate, Footer, Header },
  comments: {
    BankTable
  },
  data () {
    return {
      banks: [],
      updating: null
    }
  },
  mounted () {
    this.banks = this.fetchBanks()
  },
  computed: {
    modalShow: {
      get () {
        return this.updating !== null
      },
      set (value) {
        if (!value) {
          this.updating = null
        }
      }
    }
  },
  methods: {
    fetchBanks () {
      return [
        { id: 1, name: 'Банк1', rate: 10, maxLoan: 200000, minPayment: 20000, term: 48 },
        { id: 2, name: 'Банк2', rate: 15, maxLoan: 550000, minPayment: 40000, term: 48 },
        { id: 3, name: 'Банк3', rate: '', maxLoan: '', minPayment: '', term: '' }
      ]
    },
    remove (id) {
      this.banks = this.banks.filter(b => b.id !== id)
    },
    edit (id) {
      this.updating = this.banks.find(b => b.id === id)
    },
    cancelEdit () {
      this.modalShow = false
    },
    update ({ id, data }) {
      this.banks = this.banks.map(b => b.id === id ? data : b)
      this.modalShow = false
    }
  }
}
</script>

<style scoped>

</style>
